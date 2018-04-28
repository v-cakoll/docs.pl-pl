### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF układu zaokrąglania marginesu został zmieniony

|   |   |
|---|---|
|Szczegóły|Sposobu marginesy są zaokrąglane i obramowań i tła wewnątrz ich została zmieniona. W wyniku tej zmiany:<ul><li>Szerokość lub wysokość elementów może zwiększać i zmniejszać co najwyżej jeden piksel.</li><li>Umieszczanie obiektu można przenieść co najwyżej jeden piksel.</li><li>Elementy wyśrodkowany można pionie lub poziomie od środka co najwyżej jeden piksel.</li></ul>Domyślnie ten nowy układ jest włączone tylko dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.|
|Sugestia|Ponieważ ta modyfikacja zwykle wyeliminować wycinka prawej lub dolnej formantów WPF w DPIs wysoki, aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na .NET Framework 4.6 włączyć do tego nowe zachowanie, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;</code>aplikacji docelowych programu .NET Framework 4.6, które mają formantów WPF do renderowania przy użyciu poprzedniej algorytmu układu można to zrobić, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;</code>.|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Przekierowania|

