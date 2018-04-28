### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Niepoprawna implementacja MemberDescriptor.Equals

|   |   |
|---|---|
|Szczegóły|Oryginalnego wdrożenia &quot;jest równe&quot; metoda została porównanie dwóch właściwości inny ciąg z obiekty należące do porównania: Nazwa kategorii do ciągu opisu. Poprawka jest porównanie &quot;kategorii&quot; pierwszego obiektu &quot;kategorii&quot; drugi z nich i &quot;opis&quot; do &quot;opis&quot;. Wartość konfiguracji MemberDescriptorEqualsReturnsFalseIfEquivalent można ustawić wartość true, aby zrezygnować z nowe zachowanie, jeśli celem 4.6.2 lub wartość false, aby włączyć tę poprawkę, gdy obiektem docelowym wersja platformy jest poniżej 4.6.2.|
|Sugestia|Jeśli aplikacja jest zależna od MemberDescriptor.Equals czasami zwrócenie wartości false jeśli deskryptory są równoważne i przeznaczonych 4.6.2 wersji programu .NET Framework, masz kilka opcji:<ol><li>Zmiany kodu do porównania &quot;kategorii&quot; i &quot;opis&quot; pól oprócz ręcznego uruchamiania metody Equals.</li><li>Zrezygnować z tę zmianę, dodając następującą wartość do pliku app.config:</li></ol><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Jeśli Twoje cele aplikacji 4.6.1 lub starszej wersji programu .NET Framework, a zmiana ta jest włączona, można ustawić przełącznika zgodności na wartość false, dodając następującą wartość do pliku app.config:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

