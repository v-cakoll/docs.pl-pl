### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Zezwalaj na znaki kontrolne Unicode dwukierunkowego na identyfikatory URI

|   |   |
|---|---|
|Szczegóły|Unicode określa kilku znaków specjalnych kontroli służy do określania orientacji tekstu. W poprzednich wersjach programu .NET Framework te znaki zostały niepoprawnie usunięte z wszystkie identyfikatory URI, nawet jeśli były obecne w postaci kodowany w formacie %. Aby lepiej wykonaj [RFC 3987](http://tools.ietf.org/html/rfc3987), możemy teraz zezwolić na te znaki w identyfikatorów URI. Gdy znaleziono Niezakodowane w identyfikatorze URI, są one zakodowane w procentach. Gdy znaleziono procent, kodowane są pozostawiane jako — jest.|
|Sugestia|Dla aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.2 Obsługa jest domyślnie włączona dwukierunkowe znaki Unicode. Jeśli ta zmiana jest niepożądane, można ją wyłączyć, dodając następujące [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączyć się do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje docelowe wcześniejszych wersji programu .NET Framework, które działają w ramach wersji w programie .NET Framework 4.7.2, obsługę znaków dwukierunkowy Unicode jest domyślnie wyłączone. Możesz je włączyć, dodając następujące [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączyć się do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracji aplikacji::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

