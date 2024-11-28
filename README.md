# Bildverarbeitung
# **Zusammenfassung Woche 1: Grundlagen der digitalen Bildverarbeitung**
## **Klausurrelevante Inhalte**

### **1. Definition und Ziel der digitalen Bildverarbeitung**
- **Definition**: 
  Digitale Bildverarbeitung befasst sich mit der Analyse und Manipulation von Bildern, die als diskrete, N-dimensionale Funktionen dargestellt werden.
  - Bildfunktion: \( $f(\vec{x}) = I$ \), wobei:
    - \($\vec{x} = (x_1, x_2, ..., x_n)$\): räumliche Dimensionen (z. B. Pixelkoordinaten).
    - \($I = (I_1, I_2, ..., I_m)$\): Intensitätswerte (z. B. Grauwerte oder RGB-Farben).
  - Beispiel: Ein 2D-Farbbild \( $f(x, y) = (r, g, b)$ \) hat drei Kanäle für Rot, Grün und Blau.

- **Ziele**:
  - Verbesserung der Bildqualität (z. B. Rauschunterdrückung, Kontrastanpassung).
  - Extraktion nützlicher Informationen (z. B. Kanten, Objekte).
  - Automatische Verarbeitung und Analyse (z. B. für medizinische Bilder, Überwachungssysteme).

---

### **2. Eigenschaften digitaler Bilder**
1. **Auflösung**:
   - Anzahl der Pixel in horizontaler und vertikaler Richtung.
   - Höhere Auflösung → mehr Details.
   
2. **Farbtiefe**:
   - Anzahl der möglichen Grau- oder Farbwerte pro Pixel.
   - Beispiel: 8-Bit-Bild → 256 Grauwerte (0–255).

3. **Farbräume**:
   - Grauwerte: 1 Kanal (nur Intensität).
   - RGB: 3 Kanäle (Rot, Grün, Blau).
   - Weitere: HSV, CMYK, etc.

4. **Histogramm**:
   - Darstellung der Häufigkeit von Intensitätswerten in einem Bild.
   - Beispiel:
     - X-Achse: Grauwerte (z. B. 0–255).
     - Y-Achse: Anzahl der Pixel für jeden Grauwert.

---

### **3. Bildverarbeitungspipeline**
Die Bildverarbeitung umfasst mehrere Schritte:
1. **Bildakquisition**:
   - Umwandlung von analogen Daten (z. B. Licht) in ein digitales Bild (durch Kameras oder Sensoren).

2. **Bildverbesserung**:
   - Erhöht die visuelle Qualität oder hebt wichtige Details hervor.
   - Beispiele:
     - Kontrastanpassung.
     - Rauschunterdrückung.

3. **Bildanalyse**:
   - Automatische Extraktion von Informationen (z. B. Kanten, Objekte).

4. **Bildspeicherung**:
   - Speicherung in Formaten wie PNG (verlustfrei) oder JPEG (verlustbehaftet).

---

### **4. Wichtige mathematische Grundlagen**
1. **Histogramm**:
   - Gibt die Häufigkeitsverteilung der Pixelintensitäten eines Bildes an:
     \[
     $$h(r_k) = n_k$$
     \]
     - \( $r_k$ \): Intensitätswert.
     - \( $n_k$ \): Anzahl der Pixel mit Intensität \( $r_k$ \).

2. **Normalisiertes Histogramm**:
   - Wahrscheinlichkeit der Intensitätswerte:
     \[
     $$p(r_k) = \frac{n_k}{M \cdot N}$$
     \]
     - \( M, N \): Bilddimensionen (Breite und Höhe).

---

### **5. Klausurrelevante Beispiele**
1. **Histogramm einer Grauwerte-Bildmatrix erstellen**:
   - Gegeben: Bildmatrix \( $\begin{bmatrix} 0 & 1 & 2 \\ 2 & 1 & 0 \\ 0 & 1 & 2 \end{bmatrix}$ \).
   - Berechnung:
     - Grauwerte: \( $[0, 1, 2]$ \).
     - Häufigkeit: \( $[3, 3, 3]$ \).
     - Histogramm:
       \[
       $$h(r_k) = [3, 3, 3]$$
       \]
     - Normalisiert:
       \[
       $$p(r_k) = \frac{h(r_k)}{9} = [0.33, 0.33, 0.33]$$
       \]

2. **Histogrammgleichung**:
   - Ziel: Verteilungsungleichheiten in Bildern ausgleichen (z. B. Kontraste erhöhen).
   - Berechnung der kumulierten Wahrscheinlichkeitsdichte (CDF) aus dem Histogramm:
     \[
     $$CDF(r_k) = \sum_{j=0}^k p(r_j)$$
     \]
   - Transformation:
     \[
     $$s_k = \text{round}((L-1) \cdot CDF(r_k))$$
     \]
     - \( $L$ $\): Anzahl der Grauwerte (z. B. 256 für 8-Bit-Bilder).

---

### **6. Beispielaufgaben**
1. **Histogramm erstellen**:
   - Erstelle das Histogramm für ein Bild mit den Intensitätswerten \( $[10, 20, 20, 30, 30, 30]$ \).
   - Lösung:
     - Grauwerte: \( $[10, 20, 30]$ \).
     - Häufigkeit: \( $[1, 2, 3]$ \).

2. **Histogrammgleichung**:
   - Gegeben: Histogramm \( $h(r_k) = [10, 20, 30, 40]$ \) für Grauwerte \( $r_k = [0, 1, 2, 3]$ \).
   - Berechne die CDF und transformiere die Werte:
     - \( $p(r_k) = \frac{h(r_k)}{\text{Gesamtsumme}} = [0.1, 0.2, 0.3, 0.4]$ \).
     - \( $CDF = [0.1, 0.3, 0.6, 1.0]$ \).
     - Transformierte Werte:
       \[
       $$s_k = \text{round}((3) \cdot CDF(r_k)) = [0, 1, 2, 3]$$
       \]

3. **Multiple Choice-Frage (aus der Beispielklausur)**:
   - Was beschreibt ein Histogramm?
     - a) Die Anzahl von Pixeln in einem Bild, die in bestimmte Grauwerte fallen (korrekt).
     - b) Die Menge an Aliasing in einem Bild.
     - c) Die Anzahl der Farbkanäle eines Bildes.


# **Zusammenfassung Woche 2: Intensitäts- und räumliche Filterung**

## **Klausurrelevante Inhalte**

### **1. Histogramm-Operationen**
- **Histogrammausgleich (Equalization)**:
  - Ziel: Erhöhung des Kontrasts, indem die Grauwerte gleichmäßig über den Bereich verteilt werden.
  - **Schritte**:
    1. Berechnung des Histogramms \( $h(r_k) = n_k$ \).
    2. Normalisierung: \( $p(r_k) = \frac{n_k}{M \cdot N}$ \), wobei \( M, N \) die Bilddimensionen sind.
    3. Kumulative Wahrscheinlichkeitsdichte (CDF):
       \[
       $CDF(r_k) = \sum_{j=0}^k p(r_j)$
       \]
    4. Neue Grauwerte bestimmen:
       \[
       $s_k = \text{round}((L-1) \cdot CDF(r_k))$
       \]
       - \( L \): Anzahl der möglichen Grauwerte (z. B. 256 für 8-Bit-Bilder).

- **Histogrammausgleich Anwendung**:
  - Häufig bei Bildern mit geringem Kontrast (z. B. dunkle oder blasse Bilder).
  - Beispiel: Gleichmäßige Verteilung der Pixel über den Grauwertbereich.

---

### **2. Intensitätstransformationen**
- Transformation der Grauwerte durch Funktion \( $s = T(r)$ \), wobei:
  - \( $r$ \): Eingabegrauwert.
  - \( $s$ \): Ausgabegrauwert.
  - \( $T(r)$ \): Transformation.

#### **Typen von Transformationen**:
1. **Negativbildung**:
   - Ziel: Umkehren der Grauwerte.
   - Formel: \( $s = L - 1 - r$ \), wobei \( $L$ \) die maximale Grauwertanzahl ist (z. B. 256 für 8-Bit).
   - Anwendung: Hervorhebung von Details in hellen Bereichen.
   
2. **Logarithmische Transformation**:
   - Ziel: Verstärkung dunkler Bereiche.
   - Formel: \( $s = c \cdot \log(1 + r)$ \), wobei \( $c$ \) eine Konstante ist.
   - Anwendung: Bilder mit hohem Dynamikumfang (z. B. medizinische Bilder).

3. **Potenztransformation (Gamma-Korrektur)**:
   - Ziel: Helligkeitsanpassung (Aufhellen oder Abdunkeln).
   - Formel: \( $s = c \cdot r^\gamma$ \), wobei:
     - \( $c$ \): Konstante.
     - \( $\gamma > 1$ \): Abdunkeln.
     - \( $\gamma < 1$ \): Aufhellen.

4. **Lineare Skalierung**:
   - Ziel: Normalisierung der Intensitätswerte auf einen gewünschten Bereich.
   - Formel: \( $s = \frac{r - r_{\text{min}}}{r_{\text{max}} - r_{\text{min}}} \cdot (L-1)$ \).

---

### **3. Faltung und Filterung**
- **Definition**: Ein mathematischer Operator, der ein Eingangssignal \( f(x, y) \) mit einem Filterkern \( w(x, y) \) kombiniert, um ein Ausgangssignal \( g(x, y) \) zu erzeugen.
- **Formel (2D-Faltung)**:
  \[
  $g(x, y) = \sum_{s=-\infty}^\infty \sum_{t=-\infty}^\infty w(s, t) \cdot f(x-s, y-t)$
  \]
  - \( $f(x, y)$ \): Eingabebild.
  - \( $w(s, t$)$ \): Filterkern (auch "Maske" genannt).
  - \( $g(x, y)$ \): Ergebnisbild.

#### **Typen von Filtern**:
1. **Glättungsfilter (Low-Pass)**:
   - Ziel: Reduzierung von Rauschen.
   - Beispiel: Mittelwertfilter mit einem \( $3 \times 3$ \)-Kern:
     \[
     $w = \frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$
     \]

2. **Kantenfilter (High-Pass)**:
   - Ziel: Hervorheben von Kanten.
   - Beispiel: Sobel-Filter:
     \[
     $$G_x = \begin{bmatrix} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \end{bmatrix}, \quad
     G_y = \begin{bmatrix} -1 & -2 & -1 \\ 0 & 0 & 0 \\ 1 & 2 & 1 \end{bmatrix}$$
     \]
   - Gradientberechnung: \( $G = \sqrt{G_x^2 + G_y^2}$ \).

3. **Medianfilter**:
   - Ziel: Rauschreduktion ohne Kantenglättung.
   - Vorgehen: Ersetzen jedes Pixels durch den Median seiner Nachbarpixel.

---

### **4. Klausurrelevante Beispiele**

#### **Beispiel 1: Histogrammausgleich**
- **Gegeben**: Ein Bild mit einem Histogramm \( $h(r_k) = [10, 20, 40, 30]$ \) für Grauwerte \( $r_k = [0, 1, 2, 3]$ \).
- **Lösung**:
  1. Gesamtanzahl der Pixel: \( $N = 10 + 20 + 40 + 30 = 100$ \).
  2. Normalisiertes Histogramm:
     \[$$
     p(r_k) = \frac{h(r_k)}{N} = [0.1, 0.2, 0.4, 0.3]
     $$\]
  3. CDF:
     \[
     $$CDF(r_k) = [0.1, 0.3, 0.7, 1.0]$$
     \]
  4. Transformierte Grauwerte:
     \[
     $$s_k = \text{round}((3) \cdot CDF(r_k)) = [0, 1, 2, 3]$$
     \]

#### **Beispiel 2: Anwendung eines Mittelwertfilters**
- **Gegeben**: Ein Bildausschnitt \( $f(x, y) = \begin{bmatrix} 10 & 20 & 30 \\ 40 & 50 & 60 \\ 70 & 80 & 90 \end{bmatrix}$ \).
- **Filter**: \( $3 \times 3$ \)-Mittelwertfilter \( $w = \frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$ \).
- **Lösung**: 
  1. Anwenden des Filters auf die Pixel:
     \[
     $g(2,2) = \frac{1}{9} \cdot (10 + 20 + 30 + 40 + 50 + 60 + 70 + 80 + 90) = 50$
     \]

#### **Beispiel 3: Negativbildung**
- **Gegeben**: Ein Bild mit Grauwerten \( $r = [0, 50, 100, 150, 200]$ \).
- **Formel**: \( $s = 255 - r$ \).
- **Lösung**: \( $s = [255, 205, 155, 105, 55]$ \).

---

### **5. Beispielaufgaben**
1. **Histogrammausgleich**:
   - Ein Bild hat folgende Grauwerte \( $[0, 1, 1, 2, 2, 2, 3, 3, 3, 3]$ \).
   - Erstelle das Histogramm und berechne die transformierten Werte nach Histogrammausgleich.

2. **Medianfilter**:
   - Ein Bildabschnitt lautet \( $\begin{bmatrix} 10 & 10 & 20 \\ 20 & 30 & 30 \\ 40 & 50 & 50 \end{bmatrix}$ \).
   - Wende den Medianfilter mit einem \( $3 \times 3$ \)-Fenster auf das Pixel in der Mitte an.

3. **Transformationen**:
   - Wende die Gamma-Korrektur (\( $\gamma = 0.5$ \)) auf die Grauwerte \( $[0, 64, 128, 192, 255]$ \) an.

---


# **Zusammenfassung Woche 3: Frequenzbasierte Filterung**

## **Klausurrelevante Inhalte**

### **1. Fourier-Transformation**
- **Definition**:
  - Die Fourier-Transformation zerlegt ein Signal (z. B. ein Bild) in Sinus- und Kosinuswellen unterschiedlicher Frequenzen.
  - Anwendung: Wechsel zwischen räumlichem und Frequenzbereich, z. B. zur Analyse von Kanten, Rauschen oder Bilddetails.

#### **1D-Fourier-Transformation**:
- Vorwärts:
  \[
  $$F(u) = \int_{-\infty}^\infty f(x) \cdot e^{-2\pi i ux} dx$$
  \]
  - \( $f(x)$ \): Eingangssignal.
  - \( $F(u)$ \): Frequenzspektrum.
  - \( $u$ \): Frequenzvariable.

- Rückwärts:
  \[
  $$f(x) = \int_{-\infty}^\infty F(u) \cdot e^{2\pi i ux} du$$
  \]

#### **2D-Fourier-Transformation**:
- Vorwärts:
  \[
  $$F(u, v) = \int_{-\infty}^\infty \int_{-\infty}^\infty f(x, y) \cdot e^{-2\pi i (ux + vy)} dx dy$$
  \]
  - \( $(x, y)$ \): räumliche Koordinaten.
  - \( $(u, v)$ \): Frequenzkomponenten.

- Rückwärts:
  \[
  $$f(x, y) = \int_{-\infty}^\infty \int_{-\infty}^\infty F(u, v) \cdot e^{2\pi i (ux + vy)} du dv$$
  \]

---

### **2. Eigenschaften der Fourier-Transformation**
1. **Linearität**:
   - Kombination zweier Signale: \( $\mathcal{F}[af_1 + bf_2] = a\mathcal{F}[f_1] + b\mathcal{F}[f_2]$ \).

2. **Verschiebung**:
   - Verschiebung im räumlichen Bereich führt zu Phasenänderung im Frequenzbereich:
     \[
     $$\mathcal{F}[f(x - x_0)] = e^{-2\pi i ux_0} F(u)$$
     \]

3. **Modulation**:
   - Eine Frequenzverschiebung bewirkt eine Verschiebung im Frequenzraum:
     \[
     $$\mathcal{F}[e^{2\pi i u_0 x} f(x)] = F(u - u_0)$$
     \]

4. **Zeit-Skalierung**:
   - Streckung im räumlichen Bereich bewirkt Kompression im Frequenzbereich:
     \[
     $$\mathcal{F}[f(ax)] = \frac{1}{|a|} F\left(\frac{u}{a}\right)$$
     \]

---

### **3. Filtertypen im Frequenzbereich**
1. **Tiefpassfilter (Low-Pass)**:
   - Ziel: Unterdrückung hochfrequenter Komponenten (Rauschen).
   - Beispiel: Idealer Tiefpass mit Grenzfrequenz \( $u_c$ \):
     \[
     $$H(u, v) = \begin{cases} 
     1 & \text{für } \sqrt{u^2 + v^2} \leq u_c \\ 
     0 & \text{sonst}
     \end{cases}$$
     \]

2. **Hochpassfilter (High-Pass)**:
   - Ziel: Unterdrückung niedrigfrequenter Komponenten (z. B. Hintergrundentfernung).
   - Beispiel: Idealer Hochpass mit Grenzfrequenz \( $u_c$ \):
     \[
     $$H(u, v) = \begin{cases} 
     0 & \text{für } \sqrt{u^2 + v^2} \leq u_c \\ 
     1 & \text{sonst}
     \end{cases}$$
     \]

3. **Bandpassfilter**:
   - Ziel: Durchlass bestimmter Frequenzbereiche.

---

### **4. Diskrete Fourier-Transformation (DFT)**
- Wird verwendet, um Bilder mit endlicher Auflösung zu analysieren.
- Vorwärts-DFT:
  \[
  $$F(u, v) = \sum_{x=0}^{M-1} \sum_{y=0}^{N-1} f(x, y) \cdot e^{-2\pi i \left(\frac{ux}{M} + \frac{vy}{N}\right)}$$
  \]
- Rückwärts-DFT:
  \[
  $$f(x, y) = \frac{1}{MN} \sum_{u=0}^{M-1} \sum_{v=0}^{N-1} F(u, v) \cdot e^{2\pi i \left(\frac{ux}{M} + \frac{vy}{N}\right)}$$
  \]

---

### **5. Aliasing und Nyquist-Kriterium**
- **Aliasing**:
  - Tritt auf, wenn die Abtastfrequenz zu niedrig ist und sich Frequenzen überlagern.
  - Konsequenz: Verzerrung und Informationsverlust.

- **Nyquist-Kriterium**:
  - Die Abtastfrequenz \( $f_s$ \) muss mindestens doppelt so hoch wie die höchste Signalfrequenz \( $f_{\text{max}}$ \) sein:
    \[
    $$f_s > 2 \cdot f_{\text{max}}$$
    \]

---

### **6. Gibbs-Phänomen**
- Beim Übergang zwischen hohen und niedrigen Frequenzen entstehen Überschwinger an Diskontinuitäten (z. B. bei einer Rechteckwelle).
- Auch bei steigender Anzahl von Fourier-Koeffizienten bleibt ein Überschwingen bestehen.

---

### **7. Beispielanwendungen**
#### **Beispiel 1: Fourier-Transformation eines Signals**
- **Gegeben**: Rechteckwelle \( $f(x) = 1$ \) für \( $-T/2 \leq x \leq T/2$ \), \( $f(x) = 0$ \) sonst.
- **Lösung**:
  1. Fourier-Koeffizienten berechnen:
     \[
     $$c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(x) e^{-2\pi i nx / T} dx$$
     \]
  2. Darstellung als Summe von Sinus- und Kosinusfunktionen.

#### **Beispiel 2: Tiefpassfilter**
- **Gegeben**: Ein Bild mit starkem Rauschen.
- **Lösung**:
  1. Fourier-Transformation des Bildes berechnen.
  2. Frequenzanteile oberhalb der Grenzfrequenz \( $u_c$ \) entfernen.
  3. Rücktransformation in den räumlichen Bereich.

#### **Beispiel 3: Nyquist-Kriterium**
- **Gegeben**: Ein Signal mit höchster Frequenz \( $f_{\text{max}} = 20$ \, $\text{Hz}$ \).
- **Frage**: Bestimme die minimale Abtastfrequenz.
- **Lösung**:
  \[
  $$f_s > 2 \cdot f_{\text{max}} = 40 \, \text{Hz}$$
  \]

---

### **8. Beispielaufgaben**
1. **Fourier-Transformation berechnen**:
   - Gegeben: \( $f(x) = \sin(2\pi x)$ \) für \( $x \in [0, 1]$ \).
   - Berechne die Fourier-Koeffizienten.

2. **Filterentwurf**:
   - Entwerfe einen idealen Hochpassfilter für \( $u_c = 50$ \).

3. **Nyquist-Kriterium**:
   - Gegeben: Signal mit \( $f_{\text{max}} = 10$ \, $\text{Hz}$ \).
   - Was ist die maximale Distanz zwischen zwei Abtastpunkten?

---


# **Zusammenfassung Woche 4: Transformationen und Rekonstruktionen**

## **Klausurrelevante Inhalte**

### **1. Transformationen**

#### **1.1 Radon-Transformation**
- **Definition**:
  - Die Radon-Transformation projiziert ein 2D-Bild entlang bestimmter Winkel auf eine 1D-Achse. 
  - Anwendung: Grundlagen der Computertomographie (CT).
- **Mathematische Darstellung**:
  $$
  \mathcal{R}f(\theta, r) = \int_{-\infty}^\infty \int_{-\infty}^\infty f(x, y) \delta(x \cos\theta + y \sin\theta - r) dx dy
  $$
  - \( $\delta$ \): Dirac-Delta-Funktion.
  - \( $\theta$ \): Winkel der Projektion.
  - \( $r$ \): Abstand von der Projektionsebene.

- **Wichtige Eigenschaft**:
  - Die Radon-Transformation ist eng mit der Fourier-Transformation durch den **Fourier-Slice-Theorem** verbunden:
    $$
    F(\omega, \phi) = \mathcal{F}[\mathcal{R}f(\phi, r)](\omega)
    $$
    - Die 1D-Fourier-Transformation der Projektion entspricht einem Schnitt durch die 2D-Fourier-Transformation des Originalbildes.

---

#### **1.2 Hough-Transformation**
- **Definition**:
  - Methode zur Erkennung geometrischer Formen (z. B. Linien, Kreise) durch Parametrisierung.
- **Linienerkennung**:
  - Darstellung einer Linie im Parameterraum:
    $$
    \rho = x \cos\theta + y \sin\theta
    $$
    - \( $\rho$ \): Abstand von der Linie zum Ursprung.
    - \( $\theta$ \): Winkel zwischen der Linie und der x-Achse.

- **Ablauf**:
  1. Transformiere jeden Bildpunkt in den Parameterraum.
  2. Suche Akkumulatormaxima, die möglichen Linien entsprechen.

---

#### **1.3 Bilineare Interpolation**
- **Definition**:
  - Schätzung eines Zwischenwerts in einem Gitter basierend auf den nächsten vier bekannten Werten.
- **Formel**:
  $$f(x, y) = (1 - dx)(1 - dy) f(x_1, y_1) + dx(1 - dy) f(x_2, y_1) + (1 - dx)dy f(x_1, y_2) + dx dy f(x_2, y_2)$$
  - \( $f(x_1, y_1), f(x_2, y_1), f(x_1, y_2), f(x_2, y_2)$$ \): Werte der vier umliegenden Pixel.
  - \( $dx, dy$ \): Abstände zu den Pixelkoordinaten.

---

### **2. Rekonstruktionstechniken**

#### **2.1 Rückprojektion (Backprojection)**
- **Definition**:
  - Methode zur Rekonstruktion eines Bildes aus seinen Projektionen.
- **Mathematische Darstellung**:
  $$
  f(x, y) = \int_0^\pi \mathcal{R}f(\theta, r) \, d\theta
  $$
  - Problem: Erzeugt verschwommene Rekonstruktionen aufgrund ungleichmäßiger Gewichtung.

---

#### **2.2 Gefilterte Rückprojektion (Filtered Backprojection, FBP)**
- **Definition**:
  - Rückprojektion wird mit einem Filter kombiniert, um die Bildqualität zu verbessern.
- **Ablauf**:
  1. Fourier-Transformation der Projektionen.
  2. Multiplikation mit einem Frequenzfilter (z. B. Ram-Lak-Filter):
     $$
     H(\omega) = |\omega|
     $$
  3. Rücktransformation in den Ortsraum.
  4. Anwendung der Rückprojektion.

---

#### **2.3 Algebraische Rekonstruktionstechniken (ART)**
- **Definition**:
  - Iterative Rekonstruktion durch Lösung eines Gleichungssystems.
  - Ansatz: Minimaler Fehler zwischen gemessenen Projektionen und rekonstruiertem Bild.
- **Vorteile**:
  - Funktioniert auch bei verrauschten oder unvollständigen Daten.
- **Formel (Iterative Methode)**:
  $$
  f^{(k+1)} = f^{(k)} + \lambda \cdot \frac{p_i - \sum_j a_{ij} f_j}{\sum_j a_{ij}^2} a_{ij}
  $$
  - \( $f^{(k)}$ \): Rekonstruktionswert der \( $k$ \)-ten Iteration.
  - \( $p_i$ \): Messwert der \( $i$ \)-ten Projektion.
  - \( $a_{ij}$ \): Gewichtungsfaktoren.

---

### **3. Polar-Koordinaten-System**
- **Koordinatenumwandlungen**:
  - Von kartesischen zu polaren Koordinaten:
    $$
    r = \sqrt{x^2 + y^2}, \quad \theta = \tan^{-1}\left(\frac{y}{x}\right)
    $$
  - Von polaren zu kartesischen Koordinaten:
    $$
    x = r \cos\theta, \quad y = r \sin\theta
    $$

---

### **4. Dirac-Delta-Funktion**
- **Eigenschaften**:
  - \( $\delta(x) = 0$ \) für \( $x \neq 0$ \), \( $\int_{-\infty}^\infty \delta(x) dx = 1$ \).
  - Sifting-Eigenschaft:
    $$
    \int_{-\infty}^\infty f(x) \delta(x - x_0) dx = f(x_0)
    $$

---

### **5. Klausurrelevante Beispiele**

#### **Beispiel 1: Radon-Transformation**
- **Frage**: Beschreibe die Projektion eines quadratischen Objekts entlang des Winkels \( $\theta = 45^\circ$ \).
- **Lösung**:
  - Berechne die Projektion durch Integration der Objektintensitäten entlang der Linie \( $x + y = \text{const}$ \).

---

#### **Beispiel 2: Bilineare Interpolation**
- **Gegeben**: Werte \( $f(1, 1) = 10$ \), \( $f(2, 1) = 20$ \), \( $f(1, 2) = 30$ \), \( $f(2, 2) = 40$ \).
- **Frage**: Bestimme \( $f(1.5, 1.5)$ \).
- **Lösung**:
  $$
  f(1.5, 1.5) = 0.25 \cdot 10 + 0.25 \cdot 20 + 0.25 \cdot 30 + 0.25 \cdot 40 = 25
  $$

---

#### **Beispiel 3: Hough-Transformation**
- **Frage**: Welche Werte im Parameterraum entsprechen der Linie \( $y = 2x + 1$ \)?
- **Lösung**:
  - Parametrisiere die Linie: \( $\rho = x \cos\theta + y \sin\theta$ \).
  - Löse für verschiedene Winkel \( $\theta$ \)$.

---

### **6. Beispielaufgaben**
1. **Radon-Transformation**:
   - Erkläre den Zusammenhang zwischen der Radon-Transformation und der Fourier-Transformation.

2. **Interpolation**:
   - Gegeben: Punkte \( $(1,1), (2,1), (1,2), (2,2)$ \) mit bekannten Werten. Berechne den interpolierten Wert an \( $(1.8, 1.2)$ \).

3. **Hough-Transformation**:
   - Beschreibe den Parameterraum einer Kreisgleichung.

---


# **Zusammenfassung Woche 5: Bildkompression**

## **Klausurrelevante Inhalte**

### **1. Grundlagen der Bildkompression**
- **Ziel**:
  - Reduzierung der Datenmenge bei gleichzeitiger Erhaltung der wichtigen Informationen im Bild.
  - **Anwendungen**: Speicherplatzersparnis, schnellere Datenübertragung (z. B. JPEG, PNG).

- **Arten der Kompression**:
  1. **Verlustfreie Kompression**:
     - Keine Information geht verloren.
     - Beispiele: Huffman-Codierung, LZW (GIF, PNG).
  2. **Verlustbehaftete Kompression**:
     - Irrelevante Details werden entfernt.
     - Beispiele: JPEG, MPEG.

- **Redundanzarten**:
  - **Codierungsredundanz**:
    - Unnötige Bits zur Darstellung der Informationen.
  - **Räumliche/zeitliche Redundanz**:
    - Wiederholungen in benachbarten Pixeln oder Frames.
  - **Irrelevanz**:
    - Informationen, die für das menschliche Auge unbemerkt bleiben.

---

### **2. Wichtige Maße**
1. **Kompressionsverhältnis**:
   - Gibt an, wie stark die Daten reduziert wurden:
     $$
     C = \frac{b}{b'}
     $$
     - $b$: Anzahl der Bits vor der Kompression.
     - $b'$: Anzahl der Bits nach der Kompression.

2. **Redundanz**:
   - Anteil der entfernten Daten:
     $$
     R = 1 - \frac{1}{C} = 1 - \frac{b'}{b}
     $$

3. **Entropie**:
   - Durchschnittliche Informationsmenge pro Symbol:
     $$
     H = -\sum_{i=1}^n p(a_i) \log_2 p(a_i)
     $$
     - $p(a_i)$: Wahrscheinlichkeit des Symbols $a_i$.

---

### **3. Verlustfreie Kompressionstechniken**

#### **3.1 Huffman-Codierung**
- **Definition**:
  - Methode zur optimalen Codierung von Symbolen basierend auf ihren Wahrscheinlichkeiten.
  - Kürzere Codes für häufigere Symbole.
- **Algorithmus**:
  1. Sortiere die Symbole nach Wahrscheinlichkeit.
  2. Kombiniere die zwei Symbole mit der geringsten Wahrscheinlichkeit.
  3. Wiederhole, bis ein Baum entsteht.
  4. Weise den Ästen 0 und 1 zu, um Codes zu erstellen.

- **Beispiel**:
  - Symbole: $A, B, C, D$ mit $p(A) = 0.4$, $p(B) = 0.3$, $p(C) = 0.2$, $p(D) = 0.1$.
  - Ergebnis:
    - $A = 0$, $B = 10$, $C = 110$, $D = 111$.

---

#### **3.2 Run-Length Coding (RLE)**
- **Definition**:
  - Wiederholungen werden durch ein Symbol und die Anzahl der Wiederholungen ersetzt.
- **Beispiel**:
  - Original: $0001110000$.
  - Komprimiert: $(0, 3), (1, 3), (0, 4)$.

---

#### **3.3 Lempel-Ziv-Welch (LZW)**
- **Definition**:
  - Kodiert wiederkehrende Zeichenfolgen in einem Wörterbuch.
  - Wird in Formaten wie GIF und TIFF verwendet.
- **Algorithmus**:
  1. Beginne mit einem initialen Wörterbuch (z. B. alle möglichen Zeichen).
  2. Füge neue Kombinationen hinzu, wenn sie auftreten.
  3. Ersetze die Zeichenfolge durch ihren Wörterbucheintrag.

---

### **4. Verlustbehaftete Kompressionstechniken**

#### **4.1 Diskrete Kosinustransformation (DCT)**
- **Definition**:
  - Wandelt das Bild von der Ortsdomäne in die Frequenzdomäne um.
  - Häufig verwendete Transformation in JPEG.
- **Formel**:
  $$
  F(u, v) = \frac{1}{4} \sum_{x=0}^{N-1} \sum_{y=0}^{N-1} f(x, y) \cos\left[\frac{\pi (2x+1)u}{2N}\right] \cos\left[\frac{\pi (2y+1)v}{2N}\right]
  $$
  - $f(x, y)$: Intensitätswert bei $(x, y)$.
  - $F(u, v)$: DCT-Koeffizient.

- **JPEG-Kompression**:
  1. Bild in $8 \times 8$ Blöcke unterteilen.
  2. Anwenden der DCT auf jeden Block.
  3. Quantisieren der Koeffizienten (Entfernen kleiner Werte).
  4. Speicherung der verbleibenden Werte.

---

#### **4.2 Quantisierung**
- **Definition**:
  - Reduktion der Genauigkeit der DCT-Koeffizienten.
  - Entfernt irrelevante Details.
- **Formel**:
  $$
  Q(u, v) = \text{round}\left(\frac{F(u, v)}{q(u, v)}\right)
  $$
  - $q(u, v)$: Quantisierungsmatrix.

---

#### **4.3 Subsampling**
- **Definition**:
  - Reduzierung der Auflösung in Farbbildern, da das menschliche Auge weniger empfindlich auf Farbdetails ist.
  - Beispiel: 4:2:2- oder 4:2:0-Schema (Reduktion der Chrominanz).

---

### **5. Beispielanwendungen**

#### **Beispiel 1: Huffman-Codierung**
- **Gegeben**: Symbole $A, B, C$ mit $p(A) = 0.5$, $p(B) = 0.3$, $p(C) = 0.2$.
- **Lösung**:
  1. Erstelle den Baum:
     - Kombiniere $B$ und $C$: $p = 0.5$.
     - Kombiniere mit $A$: Finaler Baum.
  2. Codes:
     - $A = 0$, $B = 10$, $C = 11$.

#### **Beispiel 2: JPEG-Kompression**
- **Gegeben**: Ein $8 \times 8$ Block mit Intensitätswerten.
- **Frage**: Wende die DCT an und quantisiere die Werte.
- **Lösung**:
  1. Berechne die DCT-Koeffizienten mit der DCT-Formel.
  2. Quantisiere die Koeffizienten mit einer gegebenen Quantisierungsmatrix.

#### **Beispiel 3: Kompressionsverhältnis**
- **Gegeben**: Originalbildgröße $b = 1 \, \text{MB}$, komprimiertes Bild $b' = 250 \, \text{kB}$.
- **Frage**: Berechne das Kompressionsverhältnis und die Redundanz.
- **Lösung**:
  $$
  C = \frac{1 \, \text{MB}}{0.25 \, \text{MB}} = 4, \quad R = 1 - \frac{1}{4} = 0.75 = 75\%
  $$

---

### **6. Beispielaufgaben**
1. **Huffman-Codierung**:
   - Gegeben: Wahrscheinlichkeiten $p(A) = 0.4$, $p(B) = 0.3$, $p(C) = 0.2$, $p(D) = 0.1$. Erstelle den Huffman-Code.
   
2. **Run-Length Coding**:
   - Gegeben: Sequenz $11110000$. Kodieren Sie die Sequenz.

3. **JPEG-Quantisierung**:
   - Gegeben: DCT-Koeffizient $F(u, v) = 64$, Quantisierungsmatrixwert $q(u, v) = 8$. Quantisiere den Wert.

---


# **Zusammenfassung Woche 6: Segmentierung**

## **Klausurrelevante Inhalte**

### **1. Definition der Segmentierung**
- **Segmentierung**: 
  - Prozess der Unterteilung eines Bildes in sinnvolle Regionen (z. B. Objekte, Hintergrund).
  - Ziel: Regionen \( R_1, R_2, ..., R_n \) definieren, die folgende Kriterien erfüllen:
    1. \( \bigcup_{i=1}^n R_i = R \) (komplette Abdeckung des Bildbereichs \( R \)).
    2. \( R_i \cap R_j = \emptyset \) für \( i \neq j \) (Regionen sind disjunkt).
    3. \( Q(R_i) = \text{True} \) für jedes \( R_i \) (jedes Segment erfüllt ein Merkmal \( Q \)).
    4. \( Q(R_i \cup R_j) = \text{False} \) für angrenzende Regionen \( R_i \) und \( R_j \) (Merkmale unterscheiden sich).

---

### **2. Ansätze zur Segmentierung**

#### **2.1 Schwellenwertverfahren**
- **Definition**: 
  - Pixel werden anhand ihrer Intensität in Gruppen unterteilt.
- **Globale Schwelle**:
  - Eine einzige Schwelle \( T \) wird für das gesamte Bild verwendet.
  - Formel:
    $$
    g(x, y) = 
    \begin{cases} 
      1 & \text{wenn } f(x, y) \geq T \\
      0 & \text{sonst} 
    \end{cases}
    $$
- **Otsu-Algorithmus**:
  - Automatische Berechnung der optimalen Schwelle \( T \), indem die Varianz zwischen den Klassen maximiert wird.

#### **2.2 Kantenbasierte Segmentierung**
- **Definition**:
  - Kanten werden durch Gradientenänderungen im Bild erkannt.
- **Sobel-Operator**:
  - Gradientenberechnung:
    $$
    \nabla f = \sqrt{g_x^2 + g_y^2}
    $$
    - \( g_x \): Gradient in x-Richtung.
    - \( g_y \): Gradient in y-Richtung.
- **Kantenerkennung**:
  - Bildbereiche mit hohen Gradientenwerten markieren Kanten.

#### **2.3 Regionenbasierte Segmentierung**
- **Region Growing**:
  - Startpunkt (Seed) wird gewählt, von dem aus benachbarte Pixel mit ähnlichen Eigenschaften (z. B. Intensität) hinzugefügt werden.
- **Region Splitting and Merging**:
  - Bild wird initial in große Regionen unterteilt, die bei Bedarf weiter geteilt oder zusammengeführt werden.

---

### **3. Morphologische Operationen**
- **Definition**:
  - Werkzeuge zur Bearbeitung von Formen in binären Bildern, basierend auf Mengenoperationen.
- **Grundlegende Operationen**:
  1. **Erosion**:
     - Entfernt Pixel an den Rändern von Objekten.
     - Formel:
       $$
       A \ominus B = \{ z \mid B_z \subseteq A \}
       $$
       - \( A \): Eingabeobjekt.
       - \( B \): Strukturelement.
  2. **Dilatation**:
     - Fügt Pixel zu den Rändern von Objekten hinzu.
     - Formel:
       $$
       A \oplus B = \{ z \mid (B^z \cap A) \neq \emptyset \}
       $$
       - \( B^z \): Reflektiertes Strukturelement.
  3. **Öffnung**:
     - Glättet Objektgrenzen, entfernt kleine Objekte:
       $$
       A \circ B = (A \ominus B) \oplus B
       $$
  4. **Schließung**:
     - Füllt kleine Lücken in Objekten:
       $$
       A \cdot B = (A \oplus B) \ominus B
       $$

---

### **4. Fortgeschrittene Operationen**

#### **4.1 Boundary Extraction**
- Definition:
  - Extraktion der äußeren Grenze eines Objekts.
- Formel:
  $$
  \text{Boundary}(A) = A - (A \ominus B)
  $$

#### **4.2 Hit-or-Miss-Transformation**
- **Definition**:
  - Erkennt spezifische Formen in binären Bildern.
- **Formel**:
  $$
  I \odot B = (A \ominus B_1) \cap (A^c \ominus B_2)
  $$
  - \( B_1, B_2 \): Strukturelemente.

#### **4.3 Lochfüllung**
- **Definition**:
  - Füllt Löcher in Objekten, ohne die äußeren Grenzen zu durchbrechen.
- **Iterativer Algorithmus**:
  $$
  X_k = (X_{k-1} \oplus B) \cap I^c
  $$
  - \( X_0 \): Startpunkt (ein Pixel im Loch).
  - \( I^c \): Komplement des Eingabebildes.

#### **4.4 Thinning (Dünnung)**
- **Definition**:
  - Reduziert Objekte zu einer einpixelbreiten Linie.
- **Formel**:
  $$
  A \odot B = A \cap (A \oplus B)^c
  $$

---

### **5. Beispielanwendungen**

#### **Beispiel 1: Otsu-Schwellenwert**
- **Gegeben**: Histogramm mit Intensitätswerten $[0, 1, 2, 3]$ und Häufigkeiten $[10, 20, 40, 30]$.
- **Aufgabe**: Berechne die optimale Schwelle $T$.
- **Lösung**:
  1. Berechne Wahrscheinlichkeiten: $p(r_k) = \frac{n_k}{N}$.
  2. Finde $T$, das die Varianz zwischen den Klassen maximiert.

---

#### **Beispiel 2: Morphologische Operationen**
- **Gegeben**: Binärbild mit einem Objekt und Strukturelement $B = 3 \times 3$.
- **Aufgabe**: Führe Erosion und Dilatation durch.
- **Lösung**:
  - Erosion entfernt alle Randpixel, die nicht vollständig von $B$ abgedeckt werden.
  - Dilatation fügt Pixel hinzu, die mindestens teilweise von $B$ überdeckt werden.

---

#### **Beispiel 3: Kantenfindung mit Sobel-Operator**
- **Gegeben**: Grauwertbild $f(x, y)$.
- **Aufgabe**: Berechne den Gradient \( \nabla f \).
- **Lösung**:
  1. Wende die Sobel-Filter $G_x$ und $G_y$ an.
  2. Berechne:
     $$
     \nabla f = \sqrt{G_x^2 + G_y^2}
     $$

---

### **6. Beispielaufgaben**
1. **Schwellenwertverfahren**:
   - Gegeben: Bild mit Intensitätswerten $[0, 50, 100, 150, 200]$. Finde die Schwelle $T$, um Vordergrund und Hintergrund zu trennen.
   
2. **Morphologische Operationen**:
   - Wende Öffnung und Schließung auf ein Binärbild mit kleinen Objekten und Lücken an.

3. **Kantenerkennung**:
   - Gegeben: Ein Bild mit sichtbaren Kanten. Wende den Sobel-Operator an, um die Kanten zu detektieren.

---


# **Zusammenfassung Woche 7: Merkmalsextraktion und Klassifikation**

## **Klausurrelevante Inhalte**

### **1. Merkmalsextraktion**
- **Definition**:
  - Prozess zur Identifikation und Beschreibung relevanter Eigenschaften eines Bildes (z. B. Kanten, Texturen, Formen).
  - Ziel: Reduktion der Bilddaten auf aussagekräftige Informationen für Analyse oder Klassifikation.

---

### **2. Merkmalsarten**
1. **Punktbasierte Merkmale**:
   - Ecken, Knotenpunkte.
   - Erkennung durch Gradientenanalyse (z. B. Harris-Corner-Detektor).

2. **Kantenbasierte Merkmale**:
   - Detektion von Kanten (z. B. Sobel- oder Canny-Operator).

3. **Regionale Merkmale**:
   - Basieren auf zusammenhängenden Pixelgruppen mit ähnlichen Eigenschaften.
   - Beispiele: Flächen, Texturen.

4. **Formmerkmale**:
   - Beschreibung von Objekten:
     - Umfang, Fläche, Kompaktheit, Exzentrizität.

---

### **3. Merkmalsbeschreibung**
- **Feature-Vektoren**:
  - Eine Menge von Merkmalen wird in einem $n$-dimensionalen Vektor zusammengefasst:
    $$
    \mathbf{x} = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}
    $$
    - Beispiel: Farbwerte $ \mathbf{x} = \begin{bmatrix} r \\ g \\ b \end{bmatrix} $.

- **Invarianz**:
  - Merkmalsbeschreibungen sollten robust gegen Änderungen wie Translation, Rotation oder Skalierung sein.

---

### **4. Kantenbasierte Methoden**

#### **4.1 Sobel-Operator**:
- Gradientenberechnung zur Erkennung von Kanten:
  $$
  \nabla f = \sqrt{G_x^2 + G_y^2}
  $$
  - $G_x, G_y$: Gradienten in $x$- und $y$-Richtung.

#### **4.2 Canny-Algorithmus**:
- Schritte:
  1. Glättung des Bildes mit einem Gauß-Filter.
  2. Berechnung der Gradienten.
  3. Anwendung von Schwellenwerten (Hysterese).

---

### **5. Formenbeschreibung**

#### **5.1 Grundlegende Formmerkmale**
1. **Kompaktheit**:
   - Verhältnis von Fläche zu Umfang:
     $$
     C = \frac{p^2}{A}
     $$
     - $p$: Umfang, $A$: Fläche.

2. **Kreisförmigkeit**:
   - Verhältnis der Fläche eines Objekts zu einem Kreis mit gleichem Umfang:
     $$
     \text{Circularity} = \frac{4\pi A}{p^2}
     $$

3. **Exzentrizität**:
   - Verhältnis der Hauptachsen eines Ellipsoids:
     $$
     \text{Eccentricity} = \frac{\sqrt{a^2 - b^2}}{a}
     $$
     - $a, b$: Längen der Haupt- und Nebenachsen.

#### **5.2 Fourier-Beschreibung von Formen**
- Kontur wird durch Fourier-Koeffizienten beschrieben:
  $$
  s(k) = x(k) + iy(k)
  $$
  - $x(k), y(k)$: Punkte auf der Kontur.

---

### **6. Texturmerkmale**
- **Definition**:
  - Charakterisierung der Bildregion durch Wiederholungsmuster oder Intensitätsvariation.

#### **6.1 Statistische Momente**:
- Maße für Verteilungen von Grau- oder Farbwerten.
  1. **Varianz (Kontrast)**:
     $$
     \mu_2 = \sum_i (z_i - m)^2 p(z_i)
     $$
     - $m$: Mittelwert.
  2. **Schiefe (Skewness)**:
     $$
     \mu_3 = \sum_i (z_i - m)^3 p(z_i)
     $$
  3. **Wölbung (Kurtosis)**:
     $$
     \mu_4 = \sum_i (z_i - m)^4 p(z_i)
     $$

#### **6.2 Co-Occurrence-Matrix**:
- Beschreibt Häufigkeit von Pixelpaaren mit spezifischen Intensitäten:
  $$
  G(i, j) = \text{Anzahl der Pixelpaare mit } I(i) \text{ und } I(j)
  $$

- **Texturmetriken**:
  - Kontrast:
    $$
    \text{Contrast} = \sum_{i,j} (i - j)^2 G(i, j)
    $$
  - Homogenität:
    $$
    \text{Homogeneity} = \sum_{i,j} \frac{G(i, j)}{1 + |i - j|}
    $$

---

### **7. Klassifikation**

#### **7.1 Principal Component Analysis (PCA)**
- **Definition**:
  - Reduktion der Dimensionalität eines Merkmalsraums, basierend auf Hauptachsen (Eigenvektoren) der Kovarianzmatrix.
- **Algorithmus**:
  1. Berechne die Kovarianzmatrix:
     $$
     C = \frac{1}{n-1} \sum_{i=1}^n (\mathbf{x}_i - \overline{\mathbf{x}})(\mathbf{x}_i - \overline{\mathbf{x}})^T
     $$
  2. Bestimme die Eigenvektoren und Eigenwerte.
  3. Wähle die Hauptachsen mit den größten Eigenwerten.

#### **7.2 Scale Invariant Feature Transform (SIFT)**
- **Definition**:
  - Extraktion von merkmalreichen Punkten (Keypoints), die robust gegenüber Skalierung, Rotation und Beleuchtung sind.
- **Schritte**:
  1. Erstellung einer Skalenraumdarstellung.
  2. Erkennung von stabilen Extrema.
  3. Beschreibung durch einen 128-dimensionalen Vektor.

---

### **8. Beispielanwendungen**

#### **Beispiel 1: Formmerkmale**
- **Gegeben**: Ein Objekt mit $p = 20$, $A = 10$.
- **Frage**: Berechne Kompaktheit und Kreisförmigkeit.
- **Lösung**:
  $$
  C = \frac{20^2}{10} = 40, \quad \text{Circularity} = \frac{4\pi \cdot 10}{20^2} \approx 0.628
  $$

#### **Beispiel 2: Co-Occurrence-Matrix**
- **Gegeben**: Intensitätswerte $[0, 1]$.
- **Frage**: Erstelle die Co-Occurrence-Matrix und berechne den Kontrast.
- **Lösung**:
  - Matrix:
    $$
    G = \begin{bmatrix} 2 & 1 \\ 1 & 3 \end{bmatrix}
    $$
  - Kontrast:
    $$
    \text{Contrast} = (0-1)^2 \cdot 1 + (1-0)^2 \cdot 1 = 2
    $$

#### **Beispiel 3: PCA**
- **Gegeben**: Datenpunkte in einem 2D-Raum.
- **Frage**: Führe PCA durch und bestimme die Hauptachsen.
- **Lösung**:
  1. Kovarianzmatrix berechnen.
  2. Eigenvektoren und Eigenwerte bestimmen.

---

### **9. Beispielaufgaben**
1. **Texturmerkmale**:
   - Berechne Varianz und Schiefe für eine gegebene Verteilung $[1, 2, 3]$.

2. **Formbeschreibung**:
   - Gegeben: Objekt mit Hauptachse $a = 10$, Nebenachse $b = 5$. Berechne die Exzentrizität.

3. **Klassifikation mit PCA**:
   - Führe PCA auf einem 3D-Datensatz durch und reduziere ihn auf 2D.

---
