# AI_Minor
Countdown Timer using Python
import time
import threading

class CountdownTimer:
    def __init__(self, duration):
        self.duration = duration
        self.paused = False
        self.running = False
        self.countdown_thread = None

    def start(self):
        self.running = True
        self.countdown_thread = threading.Thread(target=self.run_timer)
        self.countdown_thread.start()

    def pause(self):
        self.paused = True

    def resume(self):
        self.paused = False

    def stop(self):
        self.running = False

    def reset(self, duration):
        self.duration = duration
        self.running = False
        self.paused = False

    def run_timer(self):
        while self.duration > 0 and self.running:
            if not self.paused:
                print(self.duration)
                self.duration -= 1
            time.sleep(1)

if __name__ == '__main__':
    timer = CountdownTimer(10)  # Set your desired duration here

    timer.start()
    time.sleep(5)  # Simulating some time passing

    timer.pause()
    time.sleep(2)  # Simulating some time passing

    timer.resume()
    time.sleep(3)  # Simulating some time passing

    timer.reset(15)  # Resetting the timer to 15 seconds

    timer.start()
    time.sleep(10)  # Simulating some time passing

    timer.stop()
