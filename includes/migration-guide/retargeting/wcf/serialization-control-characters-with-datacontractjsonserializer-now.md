### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializacja znaków kontrolnych, za pomocą klasy DataContractJsonSerializer jest teraz zgodna z wersji ECMAScript 6 i V8

|   |   |
|---|---|
|Szczegóły|W .NET framework 4.6.2 i wcześniejszymi wersjami <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> nie serializować niektóre znaki kontrolne specjalnych, takich jak \b \f i \t w sposób, który był zgodny ze standardami w wersji ECMAScript 6 i V8. Począwszy od programu .NET Framework 4.7 serializacji te znaki kontrolne jest zgodny z wersji ECMAScript 6 i V8.|
|Sugestia|W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.7 ta funkcja jest włączona domyślnie. Jeśli to zachowanie nie jest pożądane, można zrezygnować z tej funkcji, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

