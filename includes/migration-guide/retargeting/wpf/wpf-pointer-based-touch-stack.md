### <a name="wpf-pointer-based-touch-stack"></a>WPF Touch oparte na wskaźnik stosu

|   |   |
|---|---|
|Szczegóły|Ta zmiana dodaje możliwość włączenia opcjonalne WM_POINTER na podstawie stosu touch/pióro WPF.  Deweloperów, którzy nie zostanie jawnie włączona to powinny być widoczne nie zmiany w zachowaniu touch/pióro WPF. Bieżący znane problemy z opcjonalne WM_POINTER na podstawie touch/pióro stosu:<ul><li>Brak obsługi pisma odręcznego w czasie rzeczywistym.</li><li>Podczas pisania odręcznego i StylusPlugins będą nadal działać, będą przetwarzane w wątku interfejsu użytkownika, co może prowadzić do niskiej wydajności.</li><li>Zachowania zmian z powodu zmian w ramach podwyższenia poziomu z touch/pióro zdarzenia do zdarzenia myszy</li><li>Manipulowanie może zachowywać się inaczej</li><li>Przeciągnij i upuść nie zostanie wyświetlone odpowiednie opinię dotyczącą wprowadzania dotykowego</li><li>Nie dotyczy to wprowadzania danych piórem</li><li>Nie można zainicjować przeciągnij i upuść zdarzeń touch/pióra</li><li>To potencjalnie zawieszenie aplikacji, dopóki nie zostanie wykryty wejście myszy.</li><li>Zamiast tego deweloperzy należy zainicjować przeciągnij i upuść z zdarzeń myszy.</li></ul>|
|Sugestia|Deweloperów, którzy chcą włączyć ten stos można dodać/merge następujące polecenie, aby ich stosowania pliku App.config:<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Usunięcie tej lub ustawienie wartości FALSE spowoduje wyłączenie tego opcjonalne stosu. Należy pamiętać, że ten stos jest dostępna tylko na Windows Update twórców 10 lub nowszym.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowania|

