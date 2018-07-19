### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>Uwzględnia wszystkie claimTypes X509CertificateClaimSet.FindClaims

|   |   |
|---|---|
|Szczegóły|W aplikacjach przeznaczonych dla platformy .NET Framework 4.6.1, jeśli X509 zestawu oświadczeń jest inicjowany z certyfikatu, który ma wiele wpisów DNS w jego polu SAN <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda próbuje dopasować argument typu oświadczenia w przypadku wszystkich wpisów DNS. W przypadku aplikacji przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda próbuje dopasować argument typu oświadczenia tylko w przypadku ostatni wpis DNS.|
|Sugestia|Ta zmiana dotyczy tylko aplikacji przeznaczonych dla platformy .NET Framework 4.6.1. Ta zmiana może być wyłączona (lub włączona, jeśli elementem docelowym pre-4.6.1) za pomocą [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) zgodności przełącznika.|
|Zakres|Pomocnicza|
|Wersja|4.6.1|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

