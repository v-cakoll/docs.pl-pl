---
title: AppContextSwitchOverrides, element
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 8d5cd73bb9393533cb669581420e24297cb5ff71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102934"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides>, element

Definiuje jeden lub więcej przełączników używanych przez <xref:System.AppContext> klasę, aby zapewnić mechanizm rezygnacji dla nowych funkcji.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<AppContextSwitchOverrides>**

## <a name="syntax"></a>Składnia

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`value`|Atrybut wymagany.<br /><br /> Definiuje jedną lub więcej nazw przełączników i ich skojarzone wartości logiczne.|

### <a name="value-attribute"></a>wartość atrybutu

|Wartość|Opis|
|-----------|-----------------|
|"nazwa = wartość"|Wstępnie zdefiniowana nazwa przełącznika wraz z jego wartością ( `true` lub `false` ). Wiele par nazwa/wartość przełącznika jest oddzielonych średnikami (";"). Aby zapoznać się z listą wstępnie zdefiniowanych nazw przełączników obsługiwanych przez .NET Framework, zobacz sekcję Uwagi.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi
 Począwszy od .NET Framework 4,6, `<AppContextSwitchOverrides>` element w pliku konfiguracji umożliwia wywoływania interfejsu API, aby określić, czy aplikacja może korzystać z nowych funkcji, czy też zachować zgodność z poprzednimi wersjami biblioteki. Na przykład, jeśli zachowanie interfejsu API uległo zmianie między dwiema wersjami biblioteki, `<AppContextSwitchOverrides>` element umożliwia wywołujących tego interfejsu API rezygnację z nowego zachowania w wersjach biblioteki, które obsługują nową funkcję. W przypadku aplikacji, które wywołują interfejsy API w .NET Framework, `<AppContextSwitchOverrides>` element może również zezwalać wywołującym, których aplikacje są przeznaczone dla starszej wersji .NET Framework, aby zadecydować o nowych funkcjach, jeśli ich aplikacja działa w wersji .NET Framework, która zawiera tę funkcję.

 `value`Atrybut `<AppContextSwitchOverrides>` elementu składa się z pojedynczego ciągu składającego się z jednej lub więcej par nazw/wartości rozdzielanych średnikami.  Każda nazwa identyfikuje przełącznik zgodności, a jego odpowiadająca wartość jest wartością logiczną ( `true` lub `false` ), która wskazuje, czy przełącznik jest ustawiony. Domyślnie przełącznik jest `false` , a biblioteki udostępniają nową funkcję. Zapewniają one tylko poprzednie funkcje, jeśli przełącznik jest ustawiony (to oznacza, że jego wartość to `true` ). Dzięki temu biblioteki mogą udostępniać nowe zachowanie dla istniejącego interfejsu API, jednocześnie umożliwiając wywoływanie, które zależą od poprzedniego zachowania, aby zrezygnować z nowych funkcji.

.NET Framework obsługuje następujące przełączniki:

|Nazwa przełącznika|Opis|Wraca|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Kontroluje, czy Windows Presentation Foundation używa starszego algorytmu dla układu kontrolek. Aby uzyskać więcej informacji, zobacz [ograniczanie: układ WPF](../../../migration-guide/mitigation-wpf-layout.md).|Program .NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Określa, czy domyślny algorytm używany do podpisywania części pakietu przez PackageDigitalSignatureManager jest SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Gdy ustawiona na `false` , umożliwia debugowanie projektów przepływu pracy opartych na języku XAML w programie Visual Studio, gdy włączony jest standard FIPS. Bez tego <xref:System.NullReferenceException> jest zgłaszany w wywołaniach metod w zestawie System. Activities.|.NET Framework 4,7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Określa, czy suma kontrolna wystąpienia przepływu pracy w debugerze używa algorytmu MD5 lub SHA1. | .NET Framework 4,7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Określa, czy mieszanie sum kontrolnych przepływu pracy używa algorytmu SHA1 wprowadzonego jako domyślny w .NET Framework 4,7 ( `true` ) lub czy używa domyślnego algorytmu SHA256 wprowadzonego jako domyślny w .NET Framework 4,8 ( `false` ).<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.| .NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Kontroluje, czy ślady stosu uzyskują się, gdy użycie przenośnego plików PDB może obejmować plik źródłowy i informacje o wierszu. `false`Aby dołączyć plik źródłowy i informacje o wierszu; w przeciwnym razie `true` .| .NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Określa, czy <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda zgłasza wyjątek, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG. Aby uzyskać więcej informacji, zobacz [ograniczanie: ramki PNG w obiektach ikon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|Program .NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Określa <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> , czy obiekty są prawidłowo usuwane po dodaniu do kolekcji przez <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> metodę. `true`Aby zachować starsze zachowanie; `false`do usuwania wszystkich prywatnych obiektów czcionek. | .NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Określa, czy wydajność programu <xref:System.Windows.Forms.PrintPreviewDialog> jest zoptymalizowana pod kątem drukarek sieciowych. Aby uzyskać więcej informacji, zobacz [PrintPreviewDialog Control — Omówienie](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Określa, czy są wymuszane Sprawdzanie zakresu roku dla opcji wymazywania kalendarza japońskiego. `true`Aby wymusić sprawdzanie zakresu roku i `false` wyłączyć je (domyślne zachowanie). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Określa, czy tylko wartość "1" jest rozpoznawana jako pierwszy rok w ramach ery w przypadku kalendarza japońskiego podczas analizowania operacji. `true`Aby rozpoznać tylko wartość "1"; `false`Aby rozpoznać wartość "1" lub Gannen (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Określa, czy pierwszy rok ery w kalendarzu japońskim jest reprezentowany jako "1" lub Gannen w operacjach formatowania. `true`Aby sformatować pierwszy rok oceny era jako "1"; `false`Aby sformatować go jako Gannen (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Określa, czy operacje asynchroniczne nie są przepływem z kontekstu wywołującego wątku. Aby uzyskać więcej informacji, zobacz [CurrentCulture i CurrentUICulture Flow dla zadań](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|Program .NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Określa, czy <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda próbuje dopasować typ zgłoszenia tylko do ostatniego wpisu DNS. Aby uzyskać więcej informacji, zobacz [Metoda ograniczania: X509CertificateClaimSet. FindClaims](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Określa, czy zezwolić AuthorizationContext. Empty na zwracanie modyfikowalnego obiektu.|Program .NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Kontroluje, czy ścieżki dłuższe niż `MAX_PATH` (260 znaków) generują <xref:System.IO.PathTooLongException> . Aby uzyskać więcej informacji, zobacz [Obsługa długich ścieżek](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Kontroluje, czy natywne procedury systemu operacyjnego są używane do dekompresji przez <xref:System.IO.Compression.DeflateStream> klasę. `false`Aby korzystać z natywnych interfejsów API; `true`Aby użyć <xref:System.IO.Compression.DeflateStream> implementacji.| .NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Używa ukośnika odwrotnego (" \\ "), a nie ukośnika ("/") jako separatora ścieżki we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji, [Zobacz FullName.](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Określa, czy wyjątki systemu operacyjnego, które są generowane w wątkach w tle utworzonych przy użyciu <xref:System.IO.Ports.SerialPort> strumieni kończy proces.|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Kontroluje, czy jest używana normalizacja starszej ścieżki, a ścieżki URI są obsługiwane przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody i. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów: Normalizacja ścieżki](../../../migration-guide/mitigation-path-normalization.md) i [łagodzenie: sprawdzanie dwukropka Path](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Określa, czy test pod kątem równości porównuje <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> Właściwość jednego obiektu z <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> właściwością drugiego obiektu. Aby uzyskać więcej informacji, zobacz [niepoprawna implementacja MemberDescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Wyłącza sprawdzanie poprawności identyfikatora obiektu ulepszonego użycia klucza (EKU) certyfikatu. Rozszerzenie ulepszonego użycia klucza (EKU) to zbiór identyfikatorów obiektów (OID) wskazujący aplikacje, które używają klucza.|Program .NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Wyłącza funkcję BEAST w przeglądarce TLS 1.0 przed ograniczeniami protokołu SSL/TLS, uniemożliwiając korzystanie z SCH_SEND_AUX_RECORD.|Program .NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Określa, czy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy i mogą korzystać z protokołu SSL 3,0. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów: protokoły TLS](../../../migration-guide/mitigation-tls-protocols.md).|Program .NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Wyłącza przywracanie wersji SystemDefault TLS z powrotem do domyślnej wartości Tls12, Tls11, TLS.|.NET Framework 4,7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Wyłącza alerty po stronie serwera SslStream TLS.|.NET Framework 4,7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Kontroluje, czy parametry ByRef SafeArray w zdarzeniach międzyoperacyjnych modelu COM z powrotem do kodu natywnego ( `false` ) lub czy kierowanie z powrotem do kodu natywnego jest wyłączone ( `true` ).| .NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Określa, czy [Klasa DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializować niektóre znaki kontrolne w oparciu o standardy ECMAScript V6 i V8. Aby uzyskać więcej informacji, zobacz [ograniczanie: serializacji znaków kontrolnych za pomocą Klasa DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4,7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Kontroluje, czy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje wiele korekt lub tylko pojedyncze dopasowanie dla strefy czasowej. Jeśli `true` używa <xref:System.TimeZoneInfo> typu do serializacji i deserializacji danych daty i godziny; w przeciwnym razie używa <xref:System.TimeZone> typu, który nie obsługuje wielu reguł korekty.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Kontroluje, czy program <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> używa większego rozmiaru tablicy podczas serializacji obiektu i deserializacji. Ustaw ten przełącznik, aby `true` zwiększyć wydajność serializacji i deserializacji grafów dużych obiektów według typów, takich jak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . | .NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Określa, czy <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> Konstruktor ustawia właściwość nowego obiektu <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> z istniejącym odwołaniem do obiektu. Aby uzyskać więcej informacji, zobacz [ograniczanie: Identyfikator oświadczenia Konstruktor](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Określa, czy próba ponownego użycia <xref:System.Security.Cryptography.AesCryptoServiceProvider> odszyfrowywania zgłasza <xref:System.Security.Cryptography.CryptographicException> . Aby uzyskać więcej informacji, zobacz [AesCryptoServiceProvider odszyfrowujący umożliwia przekształcenie wielokrotnego użytku](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Określa, czy wartość właściwości [CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) jest obiektem [IntPtr](xref:System.IntPtr) , który reprezentuje lokalizację pamięci uchwytu okna lub czy jest to uchwyt okna (HWND). Aby uzyskać więcej informacji, zobacz [ograniczanie: CspParameters. ParentWindowHandle oczekuje elementu HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4,7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Określa, czy używanie zarządzanych klas kryptograficznych w trybie FIPS zgłasza <xref:System.Security.Cryptography.CryptographicException> ( `true` ), czy opiera się na implementacji bibliotek systemowych ( `false` ).| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedCMS to SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Kontroluje, czy <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> Metoda prawidłowo obsługuje wszystkie nazwane krzywe obsługiwane przez system operacyjny ( `false` ) lub przywraca starsze zachowanie.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedXML to SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Określa, czy `TransportWithMessageCredential` tryb zabezpieczeń zezwala na komunikaty z niepodpisanym nagłówkiem "do". Jest to przełącznik opcjonalny. Aby uzyskać więcej informacji, zobacz [zmiany w środowisku uruchomieniowym w .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Określa, czy <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Konstruktor zgłasza, <xref:System.ArgumentException> Jeśli jeden z elementów jest `null` .|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Określa, czy próba użycia certyfikatów x509 z dostawcą magazynu kluczy CSG zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|W przypadku korzystania z transportu HTTP z usługą samoobsługową ustawienie tej wartości spowoduje, `true` że program WCF zignoruje aplikację, dodając `Connection: close` nagłówek do nagłówków odpowiedzi dla żądania. Ustawienie tej wartości umożliwia `false` dodanie `Connection: close` nagłówka do nagłówków odpowiedzi, co spowoduje zamknięcie gniazda żądania po wysłaniu odpowiedzi.|Program .NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Obsługuje zakleszczenie wynikające z ograniczenia wystąpień usługi współużytkowanej do pojedynczego wątku wykonywania w danym momencie.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Wraz z programem `Switch.System.Net.DontEnableSchUseStrongCrypto` decyduje o tym, czy zabezpieczenia komunikatów WCF korzystają z protokołów tls 1,1 i tls 1,2.|.NET Framework 4,7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Wartość `false` ustawia konfigurację domyślną, aby umożliwić systemowi operacyjnemu wybór protokołu. Wartość `true` Ustawia domyślnie najwyższy dostępny protokół. (Dostępne również w rozgałęzieniu obsługi wcześniejszych wersji platformy)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Określa, czy domyślny algorytm podpisywania komunikatów dla komunikatów usługi MSMQ w programie WCF to SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Kontroluje, czy funkcja WCF używa skrótu SHA1 lub SHA256 do generowania losowych nazw dla nazwanych potoków.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Określa, czy zgłaszać [NullReferenceException](xref:System.NullReferenceException) , gdy komunikat o wyjątku ma wartość null.|.NET Framework 4,7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Określa, czy wyjątki zgłoszone podczas uruchamiania usługi są propagowane do obiektu wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Kontroluje, czy wystąpienia wykorzystują <xref:System.Threading.Timer> ulepszenia wydajności dla środowisk o dużej skali. Jeśli `true` są włączone ulepszenia wydajności; Jeśli `false` (wartość domyślna), są one wyłączone.| .NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Określa, czy niektóre znaki kodowane w procentach, które były czasami zdekodowane, są teraz ciągle kodowane w lewo. Jeśli `true` są dekodowane; w przeciwnym razie, `false` .| .NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Określa obsługę znaków dwukierunkowych Unicode w identyfikatorach URI. `true`Aby je rozdzielić z identyfikatorów URI; `false`Aby zachować i zakodować procentowo.| .NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Określa, czy Windows Presentation Foundation stosuje stary algorytm ( `true` ) lub nowy algorytm ( `false` ) w obszarze przydzielanie miejsca do \* kolumn. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów: Alokacja miejsca na kontrolce siatki do gwiazdki-Columns](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4,7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Określa, czy selektor lub kontrolka karta zawsze aktualizuje wartość wybranej właściwości Value przed podniesieniem zdarzenia zmiany zaznaczenia.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Określa, czy renderowanie wyboru na podstawie modułu nie jest dostępne dla <xref:System.Windows.Controls.TextBox> formantów i, <xref:System.Windows.Controls.PasswordBox> Aby zapobiec zamknięte tekstu ( `false` ) lub czy tekst jest renderowany tylko w warstwie modułu definiowania układu ( `true` ).| .NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Kontroluje, czy niestandardowe indeksatory IList są używane niepoprawnie ( `true` ) lub poprawnie ( `false` ) przez <xref:System.Windows.Data.Binding?displayProperty=nameWithType> klasę.| .NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Określa, czy zmiany DPI są wykonywane dla systemu (wartość `false` ) czy na monitor (wartość `true` ).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Kontroluje, czy ulepszenia zmiany rozmiarów kontrolek w <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> trakcie działania WPF są uruchamiane w trybie rozpoznawania dla poszczególnych monitorów są wyłączone ( `true` ) lub włączone ( `false` ).| .NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Określa, czy Deweloper musi specjalnie obsługiwać akcję, <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> gdy jest obecny tekst kontrolki. `true`Aby obsłużyć <xref:System.Windows.Forms.DomainUpDown.UpButton> akcję; `false` w <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> celu <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> poprawnego zsynchronizowania akcji i.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Zezwala na korzystanie z kodu, który umożliwia implementację niestandardową <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> w celu bezpiecznego filtrowania komunikatów bez zgłaszania wyjątku w przypadku <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> wywołania metody. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z niestandardowymi implementacjami IMessageFilter. PreFilterMessage](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Określa, czy <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> Właściwość zwraca kontrolę źródła, gdy użytkownik otwiera menu z formantu zagnieżdżonego <xref:System.Windows.Forms.ToolStripMenuItem> . `true`Aby zwrócić `null` , starsze zachowanie; `false` Aby zwrócić kontrolę źródła.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Określa, czy obsługa wywołania etykietki narzędzia jest wyłączona ( `true` ), czy włączona ( `false` ). Włączenie obsługi wywołania etykietki narzędzia wymaga również, aby wcześniej były dostępne starsze funkcje ułatwień dostępu zdefiniowane przez `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` i `Switch.UseLegacyAccessibilityFeatures.3` wszystkie są wyłączone (ustawione na `false` ).| .NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Określa, czy `WM_POINTER` w aplikacjach WPF jest włączony opcjonalny stos dotykowy/pióra. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z obsługą dotykową i piórem na podstawie wskaźnika](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4,7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Określa, czy domyślnym algorytmem wyznaczania wartości skrótu używanym w przypadku sum kontrolnych jest SHA256 ( `false` ) lub SHA1 ( `true` ).<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.| .NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Kontroluje, czy jest zgłaszane starsze [NullReferenceException](xref:System.NullReferenceException) zamiast wyjątku, który dokładniej wskazuje przyczynę wyjątku (na przykład [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) lub [FileNotFoundException](xref:System.IO.FileNotFoundException). Jest ona przeznaczona do użycia przez kod, który zależy od obsługi [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4,7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Kontroluje, czy mieszanie sum kontrolnych plików XOML w ramach kompilacji projektu przepływu pracy używa algorytmu MD5 ( `true` ) lub czy używają algorytmu SHA256 wprowadzonego jako domyślny w .NET Framework 4,8.<br>Ze względu na kolizje problemów z algorytmem MD5 firma Microsoft zaleca SHA256.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Kontroluje, czy mieszanie sum kontrolnych przez SqlTrackingService używa algorytmu MD5 ( `true` ) dla buforowanych ciągów lub czy używa algorytmu SHA256 wprowadzonego jako wartość domyślna w .NET Framework 4,8.<br>Ze względu na kolizje problemów z algorytmem MD5 firma Microsoft zaleca SHA256.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Kontroluje, czy mieszanie sum kontrolnych przez środowisko uruchomieniowe przepływu pracy używa algorytmu MD5 ( `true` ) dla buforowanych definicji przepływu pracy lub czy używa algorytmu SHA256 wprowadzonego jako wartość domyślna w .NET Framework 4,8.<br>Ze względu na kolizje problemów z algorytmem MD5 firma Microsoft zaleca SHA256.| .NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Kontroluje, czy funkcje ułatwień dostępu dostępne począwszy od .NET Framework 4.7.1 są włączone lub wyłączone. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Określa, czy funkcje ułatwień dostępu dostępne w .NET Framework 4.7.2 są włączone ( `false` ) czy wyłączone ( `true` ). Jeśli `true` `Switch.UseLegacyAccessibilityFeatures` musi być również `true` włączona funkcja ułatwień dostępu .NET Framework 4.7.1.| .NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Kontroluje, czy funkcje ułatwień dostępu wprowadzone w .NET Framework 4,8 są włączone ( `false` ) lub wyłączone ( `true` ). Jeśli `true` `Switch.UseLegacyAccessibilityFeatures` i `Switch.UseLegacyAccessibilityFeatures.2` musi być również `true` .| .NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Określa, czy etykietki narzędzi są wyświetlane, gdy użytkownik umieści kursor myszy nad kontrolką WPF ( `true` ) lub że są wyświetlane zarówno na fokus klawiatury, jak i za pomocą klawisza skrótu klawiaturowego ( `false` , zachowanie domyślne). W przypadku aplikacji uruchamianych w .NET Framework 4,8, ale przeznaczonych dla wcześniejszych wersji .NET Framework, włączenie obsługi zarówno klawiatury, jak i klawisza skrótu wymaga `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` Aby, i `Switch.UseLegacyAccessibilityFeatures.3` wszystkie były ustawione na `false` .| .NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Określa, czy puste sekwencje klawiszy w kluczach złożonych są ignorowane przez walidację schematu XSD. Aby uzyskać więcej informacji, zobacz [ograniczanie: sprawdzanie poprawności schematu XML](../../../migration-guide/mitigation-xml-schema-validation.md).|Program .NET Framework 4.6|

> [!NOTE]
> Zamiast dodawać `AppContextSwitchOverrides` elementy do pliku konfiguracji aplikacji, można również ustawić przełączniki programowo poprzez wywołanie `static` metody (w języku C#) lub `Shared` (w Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .

 Deweloperzy bibliotek mogą również definiować niestandardowe przełączniki, aby umożliwić wywołującym rezygnację ze zmienionych funkcji wprowadzonych w nowszych wersjach ich bibliotek. Aby uzyskać więcej informacji, zobacz <xref:System.AppContext> Klasa.

## <a name="switches-in-aspnet-apps"></a>Przełączniki w aplikacjach ASP.NET

Aplikację ASP.NET można skonfigurować do używania ustawień zgodności przez dodanie [\<Add>](../appsettings/add-element-for-appsettings.md) elementu do [\<appSettings>](../appsettings/index.md) sekcji pliku Web. config.

Poniższy przykład używa elementu, `<add>` Aby dodać dwa ustawienia do `<appSettings>` sekcji pliku Web. config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Przykład

 Poniższy przykład używa elementu, `AppContextSwitchOverrides` Aby zdefiniować pojedynczy przełącznik zgodności aplikacji, `Switch.System.Globalization.NoAsyncCurrentCulture` który uniemożliwia przepływanie kultury między wątkami w wywołaniach metod asynchronicznych.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 Poniższy przykład używa elementu, `AppContextSwitchOverrides` Aby zdefiniować dwa przełączniki zgodności aplikacji `Switch.System.Globalization.NoAsyncCurrentCulture` i `Switch.System.IO.BlockLongPaths` . Średnik oddziela dwie pary nazwa/wartość.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Eliminowanie nowych zachowań w .NET Framework 4,6 i nowszych](../../../migration-guide/mitigations.md)
- <xref:System.AppContext?displayProperty=nameWithType>
- [\<runtime>Postaci](runtime-element.md)
- [\<configuration>Postaci](../configuration-element.md)
