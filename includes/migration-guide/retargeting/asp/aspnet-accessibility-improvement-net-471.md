### <a name="aspnet-accessibility-improvement-in-net-471"></a>Zwiększenie dostępności ASP.NET w .NET 4.7.1

|   |   |
|---|---|
|Szczegóły|ASP.NET w celu ulepszania działanie formantów sieci Web ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio klientom ASP.NET lepszą obsługę.  Obejmują one następujące zmiany:<ul><li>Zmiany w implementacji Brak wzorce ułatwień dostępu interfejsu użytkownika w formantach, takie jak okna dialogowego Dodawanie pól w Kreatorze widoku szczegółów.</li><li>Zmiany w celu polepszenia wyświetlania w trybie dużego kontrastu, takich jak edytor pola modułu stronicowania danych.</li><li>Zmiany w celu polepszenia nawigacji klawiatury napotyka dla formantów, jak skonfigurować okna kontekst obiektu lub okno Konfigurowanie źródła danych.</li></ul>|
|Sugestia|**Jak zgłosić do lub z tych zmian do** aby projektanta programu Visual Studio do korzystania z tych zmian, należy uruchomić w programie .NET Framework 4.7.1 lub nowszym. Aplikacja sieci web mogą korzystać z tych zmian w jednym z następujących sposobów:<ul><li>Zainstaluj program Visual Studio 2017 15 ustęp 3 lub później, który obsługuje nowe funkcje ułatwień dostępu do następującego przełącznika AppContext domyślnie.</li><li>Opcja rezygnacji z zachowania starszych ułatwień dostępu przez dodanie **Switch.UseLegacyAccessibility** przełącznika AppContext do `<runtime>` sekcji w pliku devenv.exe.config i ustawienie jej w `false`, jako poniższy przykład Pokazuje.</li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|Przekierowania|
