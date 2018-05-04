### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF już zgłasza dla QueryViews o określonej charakterystyce

|   |   |
|---|---|
|Szczegóły|Entity Framework już zgłasza <xref:System.StackOverflowException?displayProperty=name> wyjątku, gdy aplikacja wykonuje zapytania, która obejmuje QueryView z od 0 do 1 właściwość nawigacji, który próbuje dołączyć powiązanych jednostek w ramach zapytania. Na przykład wywołując <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Sugestia|Ta zmiana wpływa tylko na kod, który używa QueryViews z 1-od 0 do 1 relacje uruchomiona kwerendę dotyczącą tego wywołania. Obejmują. Zwiększa niezawodność, a powinny być przezroczyste do niemal wszystkich aplikacji. Jednak jeśli spowoduje nieoczekiwane zachowanie, można wyłączyć ją, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|

