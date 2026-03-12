# ERRCHA RADAR v1.0 🛰️

### [RUS] Описание проекта
**ERRCHA RADAR** — это экспериментальная система акустического зондирования (Acoustic Sensing), превращающая обычные устройства в активный сонар. Проект демонстрирует, как использовать стандартные динамики и микрофоны для обнаружения объектов и измерения относительной дистанции.

#### Логика работы:
* **Передатчик (iPhone):** Генерирует непрерывную синусоидальную волну на частоте **18.5 кГц**. Это "серая зона": микрофоны её отлично фиксируют, а большинство взрослых людей уже не слышат.
* **Приемник (MacBook):** В реальном времени раскладывает входящий звук на спектр с помощью **Fast Fourier Transform (FFT)**.
* **Детекция:** Программа игнорирует весь посторонний шум, отслеживая только узкий диапазон 18.5 кГц. При приближении источника звука амплитуда на этой частоте растет, что триггерит визуальное оповещение.

#### Характеристики и ограничения:
* **Радиус работы:** Стабильно **2–3 метра** в помещении. До **5 метров** при прямой видимости.
* **Точность:** Высокая чувствительность к перемещению (реагирует на движение в пределах 5–10 см).
* **Погрешности:** * *Эффект Доплера:* При очень быстром движении пик частоты может сместиться в соседний диапазон.
    * *Интерференция:* Отражения звука от стен могут создавать "мертвые зоны".
    * *Шумы:* Свист или трение металла могут создавать помехи, хотя FFT-фильтр отсекает большинство из них.

---

### [ENG] Project Overview
**ERRCHA RADAR** is an experimental Acoustic Sensing system that transforms standard consumer electronics into an active sonar. It leverages ultrasound to detect objects and measure relative proximity without specialized hardware.

#### Core Logic:
* **The Sender (iPhone):** Emits a continuous sine wave at **18.5 kHz**. This frequency is at the edge of the human hearing range—audible to microphones but silent to most adults.
* **The Receiver (MacBook):** Performs real-time audio analysis using **Fast Fourier Transform (FFT)** via the Web Audio API.
* **Detection:** The system filters out ambient noise and monitors the specific 18.5 kHz bin. When the signal amplitude exceeds a defined threshold, an "OBJECT DETECTED" alert is triggered.

#### Technical Specs & Limitations:
* **Effective Range:** Stable up to **2–3 meters**. Up to **5 meters** with a clear line of sight.
* **Precision:** High sensitivity to movement (detects changes within 5–10 cm), but relative (not absolute) distance measurement.
* **Known Limitations:**
    * *Doppler Effect:* Rapid movement can shift the frequency, causing the signal peak to momentarily shift from the target bin.
    * *Multipath Interference:* Sound reflections from walls can create constructive or destructive interference.
    * *Environmental Noise:* High-pitched mechanical friction may cause minor interference.

---

### Технологический стек / Tech Stack
* **HTML5 / CSS3** (UI & Visualization)
* **JavaScript (Vanilla)**
* **Web Audio API** (OscillatorNode & AnalyserNode)

## Quick Start
1. Clone this repository.
2. Open `receiver.html` on your MacBook and click **"ЗАПУСТИТЬ СКАНЕР"**.
3. Open `sender.html` on your iPhone and click **"START"**.
4. Observe the signal peak on the **ERRCHA RADAR** interface.
