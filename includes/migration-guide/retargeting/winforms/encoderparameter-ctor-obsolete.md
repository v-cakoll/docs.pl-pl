### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor jest przestarzała

|   |   |
|---|---|
|Szczegóły|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor jest teraz przestarzałe i wprowadzi kompilacji ostrzeżenia, jeśli używana.|
|Sugestia|Mimo że <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor będą nadal działać, następujący Konstruktor należy użyć w celu uniknięcia ostrzeżenie przestarzałe kompilacji podczas ponownego kompilowania kodu przy użyciu narzędzi platformy .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

