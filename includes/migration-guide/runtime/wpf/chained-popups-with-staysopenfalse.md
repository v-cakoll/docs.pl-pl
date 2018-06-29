### <a name="chained-popups-with-staysopenfalse"></a>Tworzenie łańcucha wyskakujące okienka z parametrem StaysOpen = False

|   |   |
|---|---|
|Szczegóły|Wyskakujące okienko z parametrem StaysOpen = False powinien zamknięte po kliknięciu poza menu podręcznego. Gdy dwa lub więcej takich wyskakujące okienka są powiązane łańcuchem zależności (tj. jeden zawiera inny), wystąpiły problemy wiele, w tym:<ul><li>Otwórz dwa poziomy, kliknij pozycję poza P2, ale wewnątrz P1.  Nic się nie dzieje.</li><li>Otwórz dwa poziomy, kliknij pozycję poza P1.  Zamknij oba wyskakujące okienka.</li><li>Dwa poziomy otwierających i zamykających.  Spróbuj ponownie otworzyć P2.  Nic się nie dzieje.</li><li>Spróbuj otworzyć trzy poziomy.  Nie można wykonać.  (Nic się nie dzieje lub zamknąć pierwsze dwa poziomy, w zależności od tego, gdzie kliknij.) Te przypadki (i innych wariantów) teraz działać zgodnie z oczekiwaniami.</li></ul>|
|Zakres|Krawędź|
|Wersja|4.7.1|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

