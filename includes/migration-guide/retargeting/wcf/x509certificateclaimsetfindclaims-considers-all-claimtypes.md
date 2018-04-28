### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>Traktuje wszystkie claimTypes X509CertificateClaimSet.FindClaims

|   |   |
|---|---|
|Szczegóły|W aplikacjach przeznaczonych dla platformy .NET Framework 4.6.1, jeśli X509 zestaw oświadczeń jest zainicjowany z certyfikatu, który ma wiele wpisów DNS w polu sieci SAN <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda próbuje dopasować argumentu typu oświadczenia z wszystkie wpisy DNS. W przypadku aplikacji, które odnoszą się do poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda próbuje dopasować argumentu typu oświadczenia tylko w przypadku ostatni wpis DNS.|
|Sugestia|Ta zmiana wpływa tylko na aplikacji przeznaczonych dla platformy .NET Framework 4.6.1. Ta zmiana może być wyłączone (lub nie jest włączone, jeśli dotyczących wersji pre-4.6.1) z [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) zgodności przełącznika.|
|Zakres|Pomocnicza|
|Wersja|4.6.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

