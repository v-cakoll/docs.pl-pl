### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>Po usunięciu obiektu System.Threading.Tasks.Task już throw objectdisposedexception —

|   |   |
|---|---|
|Szczegóły|Z wyjątkiem <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=name> metod nie generują <xref:System.ObjectDisposedException?displayProperty=name> wyjątek po usunięciu obiektu. Ta zmiana obsługuje zadania pamięci podręcznej. Na przykład metoda może zwracać buforowane zadanie w celu reprezentowania już zakończonej operacji, zamiast przydzielać nowe zadanie. Było to niemożliwe w poprzednich wersjach programu .NET Framework, ponieważ każdy konsument zadania mógł je usunąć, co czyniło je bezużytecznym.|
|Sugestia|Należy pamiętać, że metody zadań nie może zgłaszać <xref:System.ObjectDisposedException?displayProperty=name> w przypadkach, gdy obiekt jest usunięty. Jeśli aplikacja była w zależności od tego wyjątku, aby dowiedzieć się, że zadanie zostało usunięte, należy zaktualizować jawnie sprawdzić stan zadania przy użyciu <xref:System.Threading.Tasks.Task.Status>.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

