### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>Teraz RSACng.VerifyHash zwraca wartość False dla jakiekolwiek niepowodzenie weryfikacji

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, ta metoda zwraca <strong>False</strong> samym podpisie jest nieprawidłowo sformatowany. Obecnie zwraca wartość false dla dowolnego błąd weryfikacji. .NET Framework 4.6 i 4.6.1, metoda wygeneruje <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> samym podpisie jest nieprawidłowo sformatowany.|
|Sugestia|Każdy kod, których wykonanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zamiast tego należy wykonać, jeśli uwierzytelnienie nie powiedzie się i metoda zwraca <strong>False</strong>.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

