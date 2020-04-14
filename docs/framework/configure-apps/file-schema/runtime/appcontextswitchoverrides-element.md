---
title: AppContextSwitchOverrides Element
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 95ae438e9fb52cc584d18a981bffb66147eb4a77
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242819"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> element

Definiuje jeden lub więcej przełączników <xref:System.AppContext> używanych przez klasę, aby zapewnić mechanizm rezygnacji dla nowych funkcji.

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
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
|`value`|Atrybut wymagany.<br /><br /> Definiuje jedną lub więcej nazw przełączników i skojarzonych z nimi wartości logicznych.|

### <a name="value-attribute"></a>Atrybut wartość

|Wartość|Opis|
|-----------|-----------------|
|"nazwa=wartość"|Wstępnie zdefiniowana nazwa przełącznika wraz`true` z `false`jego wartością ( lub ). Wiele par nazw przełączników/wartości jest oddzielonych średnikami (";"). Aby uzyskać listę wstępnie zdefiniowanych nazw przełączników obsługiwanych przez program .NET Framework, zobacz sekcję Uwagi.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi
 Począwszy od programu .NET Framework 4.6, `<AppContextSwitchOverrides>` element w pliku konfiguracji umożliwia wywołującym interfejs API, aby ustalić, czy ich aplikacja może korzystać z nowych funkcji lub zachować zgodność z poprzednimi wersjami biblioteki. Na przykład jeśli zachowanie interfejsu API uległo zmianie między `<AppContextSwitchOverrides>` dwiema wersjami biblioteki, element umożliwia wywołującym tego interfejsu API zrezygnować z nowego zachowania w wersjach biblioteki, które obsługują nowe funkcje. W przypadku aplikacji, które wywołują `<AppContextSwitchOverrides>` interfejsy API w programie .NET Framework, element może również umożliwić obiektom wywołującym, których aplikacje są przeznaczone dla starszej wersji programu .NET Framework, wybranie nowych funkcji, jeśli ich aplikacja jest uruchomiona w wersji programu .NET Framework, która zawiera tę funkcję.

 Atrybut `value` `<AppContextSwitchOverrides>` elementu składa się z pojedynczego ciągu, który składa się z jednego lub więcej para nazw/wartości rozdzielanych średnikami.  Każda nazwa identyfikuje przełącznik zgodności, a jego odpowiednią wartością`true` `false`jest wartość logiczna ( lub ), która wskazuje, czy przełącznik jest ustawiony. Domyślnie przełącznik jest `false`, a biblioteki zapewniają nowe funkcje. Zapewniają one tylko poprzednie funkcje, jeśli przełącznik jest ustawiony `true`(to jest jego wartość jest ). Dzięki temu biblioteki, aby zapewnić nowe zachowanie dla istniejącego interfejsu API, umożliwiając jednocześnie wywołujących, którzy zależą od poprzedniego zachowania, aby zrezygnować z nowych funkcji.

 Program .NET Framework obsługuje następujące przełączniki:

|Zmień nazwę|Opis|Wprowadzone|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Określa, czy program Windows Presentation Foundation używa starszego algorytmu dla układu sterowania. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Układ WPF](../../../migration-guide/mitigation-wpf-layout.md).|Program .NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Określa, czy domyślny algorytm używany do podpisywania części pakietu przez PackageDigitalSignatureManager jest SHA1 lub SHA256.<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Po ustawieniu `false`, umożliwia debugowanie projektów przepływu pracy opartych na XAML za pomocą programu Visual Studio, gdy fips jest włączony. Bez niego <xref:System.NullReferenceException> a jest generowany w wywołaniach metod w System.Activities zestawu.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Określa, czy suma kontrolna dla wystąpienia przepływu pracy w debugerze używa MD5 lub SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Określa, czy mieszanie sumy kontrolnej przepływu pracy używa algorytmu SHA1 wprowadzonego`true`jako domyślny w .NET Framework 4.7 ( ), czy też używa`false`domyślnego algorytmu SHA256 wprowadzonego jako domyślnego w .NET Framework 4.8 ( ).<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.| .NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Określa, czy ślady stosu uzyskuje się podczas korzystania z przenośnych plików PDB może zawierać informacje o pliku źródłowym i wierszu. `false`dołączanie informacji o pliku źródłowym i wierszu; w `true`przeciwnym razie , .| .NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Określa, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> czy metoda zgłasza wyjątek, gdy obiekt <xref:System.Drawing.Icon> ma ramki PNG. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Ramki PNG w obiektach ikon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|Program .NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Określa, <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> czy obiekty są prawidłowo usuwane po <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> dodaniu do kolekcji za pomocą metody. `true`w celu utrzymania starszego zachowania; `false` , aby usunąć wszystkie prywatne obiekty czcionek. | .NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Określa, czy wydajność <xref:System.Windows.Forms.PrintPreviewDialog> drukarek sieciowych jest zoptymalizowana pod kątem. Aby uzyskać więcej informacji, zobacz [Omówienie formantu PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Określa, czy wyegzekwowane są kontrole zakresu roku dla japońskich epok kalendarza. `true`, aby wymusić `false` sprawdzanie zakresu roku i wyłączyć je (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Określa, czy tylko "1" jest rozpoznawany jako pierwszy rok ery kalendarza japońskiego w operacjach analizowania. `true`rozpoznać tylko "1"; `false` , aby rozpoznać "1" lub Gannen (domyślne zachowanie). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Określa, czy pierwszy rok japońskiej ery kalendarza jest reprezentowany jako "1" lub Gannen w operacjach formatowania. `true`sformatowanie pierwszego roku epoki jako "1"; `false` , aby sformatować go jako Gannen (domyślne zachowanie). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|Program .NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Określa, czy operacje asynchroniczne nie pochodzą z kontekstu wątku wywołującego. Aby uzyskać więcej informacji, zobacz [CurrentCulture i CurrentUICulture przepływu między zadaniami](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|Program .NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Określa, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> czy metoda próbuje dopasować typ oświadczenia tylko do ostatniego wpisu DNS. Aby uzyskać więcej informacji, zobacz [Łagodzenie: X509CertificateClaimSet.FindClaims Metoda](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Określa, czy zezwolić AuthorizationContext.Empty na zwracanie obiektu modyfikowalnego.|Program .NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Określa, czy ścieżki `MAX_PATH` dłuższe niż (260 znaków) wrzucają plik <xref:System.IO.PathTooLongException>. Aby uzyskać więcej informacji, zobacz [Obsługa długiej ścieżki](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Określa, czy natywne procedury systemu operacyjnego <xref:System.IO.Compression.DeflateStream> są używane do dekompresji przez klasę. `false`, aby użyć natywnych interfejsów API; `true` wykorzystania <xref:System.IO.Compression.DeflateStream> implementacji.| .NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Używa ukośnika odwrotnego ("\\") zamiast ukośnika do przodu <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> ("/") jako separatora ścieżki we właściwości. Aby uzyskać więcej informacji, zobacz [Łagodzenie: ZipArchiveEntry.FullName Path Separator](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Określa, czy wyjątki systemu operacyjnego, które <xref:System.IO.Ports.SerialPort> są generowane w wątkach w tle utworzonych za pomocą strumieni zakończyć proces.|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Określa, czy normalizacja ścieżki starszej jest używana i <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> ścieżki URI są obsługiwane przez i metody. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Normalizacja ścieżki](../../../migration-guide/mitigation-path-normalization.md) i [łagodzenie: Kontrola dwukropek ścieżki](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Określa, czy test równości <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> porównuje właściwość jednego <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> obiektu z właściwością drugiego obiektu. Aby uzyskać więcej informacji, zobacz [Nieprawidłowa implementacja memberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Wyłącza sprawdzanie poprawności identyfikatora obiektów EKU (EKU) (EKU) (EKU). Rozszerzenie rozszerzonego użycia klucza (EKU) jest kolekcją identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza.|Program .NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Wyłącza ograniczenie wykorzystania przez przeglądarkę TLS1.0 w stosunku do ograniczenia SSL/TLS (BEAST) poprzez wyłączenie użycia SCH_SEND_AUX_RECORD.|Program .NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Określa, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> czy <xref:System.Net.Security.SslStream?displayProperty=nameWithType> i klasy mogą używać protokołu SSL 3.0. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Protokoły TLS](../../../migration-guide/mitigation-tls-protocols.md).|Program .NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Wyłącza wersje Protokołu TLS systemdefault, przywracając domyślnie Tls12, Tls11, Tls.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Wyłącza alerty po stronie serwera TLS SslStream.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Określa, czy parametry ByRef SafeArray na zdarzeniach`false`współdziałania COM są kierowane z`true`powrotem do kodu macierzystego ( ) lub czy kierowanie z powrotem do kodu macierzystego jest wyłączone ( ).| .NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Określa, czy [datacontractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje niektóre znaki kontrolne na podstawie standardów ECMAScript V6 i V8. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Serializacja znaków kontroli za pomocą datacontractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Określa, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> czy obsługuje wiele korekt, czy tylko pojedyncze dostosowanie dla strefy czasowej. Jeśli `true`, używa <xref:System.TimeZoneInfo> tego typu do serializacji i deserializacji danych daty i godziny; w przeciwnym razie <xref:System.TimeZone> używa typu, który nie obsługuje wielu reguł dopasowania.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Określa, <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> czy używa większego rozmiaru tablicy podczas serializacji i deserializacji obiektów. Ustaw ten `true` przełącznik, aby poprawić wydajność serializacji i deserializacji wykresów <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>dużych obiektów według typów, takich jak . | .NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Określa, <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> czy konstruktor ustawia <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> właściwość nowego obiektu z istniejącym odwołaniem do obiektu. Aby uzyskać więcej informacji, zobacz [Łagodzenie: ClaimsIdentity Constructor](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Określa, czy próba ponownego <xref:System.Security.Cryptography.AesCryptoServiceProvider> użycia deszyfratora zgłasza plik <xref:System.Security.Cryptography.CryptographicException>. Aby uzyskać więcej informacji, zobacz [AesCryptoServiceOdszywanieprovider zapewnia przekształcenie wielokrotnego użytku](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Określa, czy wartość [właściwości CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) jest [IntPtr,](xref:System.IntPtr) która reprezentuje lokalizację pamięci dojścia okna, czy też jest to uchwyt okna (HWND). Aby uzyskać więcej informacji, zobacz [Łagodzenie: CspParameters.ParentWindowHandle oczekuje HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Określa, czy korzystanie z zarządzanych klas kryptografii <xref:System.Security.Cryptography.CryptographicException> `true`w trybie FIPS rzuca (`false`) lub opiera się na implementacji bibliotek systemowych ( ).| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Określa, czy domyślnie dla niektórych operacji SignedCMS jest SHA1 lub SHA256.<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Określa, <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> czy metoda poprawnie obsługuje wszystkie nazwane krzywe`false`obsługiwane przez system operacyjny ( ) lub powraca do starszego zachowania.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Określa, czy domyślnie dla niektórych operacji SignedXML jest SHA1 lub SHA256.<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Określa, `TransportWithMessageCredential` czy tryb zabezpieczeń zezwala na wiadomości z niepodpisanym nagłówkiem "do". Jest to przełącznik opt-in. Aby uzyskać więcej informacji, zobacz [Zmiany środowiska wykonawczego w .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Określa, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> czy konstruktor <xref:System.ArgumentException> zgłasza, jeśli `null`jeden z elementów jest .|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Określa, czy próba użycia certyfikatów X509 z dostawcą magazynu kluczy CSG zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [Zabezpieczenia transportu WCF obsługuje certyfikaty przechowywane przy użyciu CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Podczas korzystania z transportu HTTP z usługą hostowania `true` samodzielnie, ustawienie tej wartości `Connection: close` powoduje WCF ignorować aplikacji dodając nagłówek do nagłówków odpowiedzi dla żądania. Ustawienie tej `false` wartości umożliwia `Connection: close` dodanie nagłówka do nagłówków odpowiedzi, co powoduje zamknięcie gniazda żądania po wysłaniu odpowiedzi.|Program .NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Obsługuje zakleszczenia, które wynikają z ograniczenia wystąpień usługi ponownego wjazdu do jednego wątku wykonywania w czasie.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Wraz `Switch.System.Net.DontEnableSchUseStrongCrypto`z , określa, czy zabezpieczenia wiadomości WCF używa TLS 1.1 i TLS 1.2.|.NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Wartość `false` ustawia domyślną konfigurację, aby umożliwić systemowi operacyjnemu wybranie protokołu. Wartość `true` ustawia domyślny do najwyższego dostępnego protokołu. (Dostępne również w zakresie obsługi gałęzi poprzednich wersji framework)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Określa, czy domyślny algorytm podpisywania wiadomości MSMQ w WCF jest SHA1 lub SHA256.<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Określa, czy WCF używa skrótu SHA1 lub SHA256 do generowania losowych nazw nazwanych potoków.<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Określa, czy zgłosić [NullReferenceException,](xref:System.NullReferenceException) gdy komunikat o wyjątku jest null.|.NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Określa, czy wyjątki zgłaszane podczas uruchamiania usługi są <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> propagowane do wywołującego metody.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Określa, <xref:System.Threading.Timer> czy wystąpienia korzystają z ulepszeń wydajności w środowiskach na dużą skalę. Jeśli `true`, ulepszenia wydajności są włączone; jeśli `false` (wartość domyślna), są one wyłączone.| .NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Określa, czy niektóre znaki zakodowane w procentach, które czasami były dekodowane, są teraz konsekwentnie zakodowane. Jeśli `true`są dekodowane; w `false`przeciwnym razie , .| .NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Określa obsługę znaków dwukierunkowych Unicode w identyfikatorach URI. `true`aby usunąć je z identyfikatorów URI; `false` , aby je zachować i zakodować procentami.| .NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Określa, czy program Windows Presentation Foundation`true`stosuje stary algorytm`false`( ) lub \*nowy algorytm ( ) przy przydzielaniu miejsca do kolumn. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Alokacja przestrzeni formantu siatki do kolumn gwiazdek](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Określa, czy selektor lub formant tabulacji zawsze aktualizuje wartość wybranej właściwości wartości przed podniesieniem zdarzenia zmiany zaznaczenia.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Określa, czy renderowanie zaznaczenia nieoparte na <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> Adornerze jest dostępne`false`dla formantów i formanty, aby`true`zapobiec okludowaniu tekstu ( ), czy też tekst jest renderowany tylko w warstwie Adornera ( ).| .NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Określa, czy niestandardowe indeksatory IList są używane niepoprawnie (`true`) lub poprawnie (`false`) przez <xref:System.Windows.Data.Binding?displayProperty=nameWithType> klasę.| .NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Określa, czy zmiany DPI występują w systemie `false`(wartość ) lub na podstawie `true`monitora (wartość ).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Określa, czy ulepszenia w określaniu <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> rozmiaru formantów w przypadku uruchomienia WPF w trybie obsługującym na monitor są wyłączone (`true`) lub włączone (`false`).| .NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Określa, czy deweloper musi specjalnie <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> obsługiwać akcję, gdy tekst formantu jest obecny. `true`do obsługi <xref:System.Windows.Forms.DomainUpDown.UpButton> akcji; `false` i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> działania, które mają być prawidłowo zsynchronizowane.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Rezygnuje z kodu, który umożliwia <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji niestandardowej bezpiecznie filtrować <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> wiadomości bez zgłaszania wyjątku, gdy metoda jest wywoływana. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Niestandardowe implementacje IMessageFilter.PreFilterMessage](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Określa, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> czy właściwość zwraca formant źródła, gdy użytkownik <xref:System.Windows.Forms.ToolStripMenuItem> otwiera menu z formantu zagnieżdżonego. `true`aby `null`powrócić, starsze zachowanie; `false` , aby przywrócić kontrolę źródła.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Określa, czy obsługa wywołania etykietki narzędzia jest wyłączona (`true`) lub włączona (`false`). Włączenie obsługi wywołania etykietki narzędzi wymaga również `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`starszych `Switch.UseLegacyAccessibilityFeatures.3` funkcji ułatwień `false`dostępu zdefiniowanych przez program , a wszystkie są wyłączone (ustawione na ).| .NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Określa, czy `WM_POINTER`opcjonalny stos dotykowy/pióro jest włączony w aplikacjach WPF. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Obsługa dotykowy i rysikowy oparty na wskaźnikach](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Określa, czy domyślnym algorytmem mieszania używanym dla`false`sum kontrolnych`true`jest SHA256 ( ) czy SHA1 ( ).<br>Ze względu na problemy z kolizją z SHA1 firma Microsoft zaleca SHA256.| .NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Określa, czy starsza [NullReferenceException](xref:System.NullReferenceException) jest zgłaszany zamiast wyjątku, który w szczególności wskazuje przyczynę wyjątku (na przykład [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) lub [FileNotFoundException](xref:System.IO.FileNotFoundException). Jest on przeznaczony do użycia przez kod, który zależy od obsługi [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Określa, czy mieszanie sumy kontrolnej plików XOML w kompilacjach`true`projektu przepływu pracy używa algorytmu MD5 ( ), czy używają algorytmu SHA256 wprowadzonego jako domyślnego w programie .NET Framework 4.8.<br>Ze względu na problemy z kolizją z MD5 firma Microsoft zaleca sha256.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Określa, czy mieszanie sumy kontrolnej przez SqlTrackingService`true`używa algorytmu MD5 ( ) dla ciągów buforowanych lub czy używa algorytmu SHA256 wprowadzonego jako domyślnego w programie .NET Framework 4.8.<br>Ze względu na problemy z kolizją z MD5 firma Microsoft zaleca sha256.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Określa, czy mieszanie sumy kontrolnej przez środowisko wykonawcze`true`przepływu pracy używa algorytmu MD5 ( ) dla definicji buforowanego przepływu pracy, czy też używa algorytmu SHA256 wprowadzonego jako domyślnego w .NET Framework 4.8.<br>Ze względu na problemy z kolizją z MD5 firma Microsoft zaleca sha256.| .NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Określa, czy funkcje ułatwień dostępu dostępne począwszy od platformy .NET Framework 4.7.1 są włączone lub wyłączone. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Określa, czy funkcje ułatwień dostępu dostępne w systemie .NET`false`Framework 4.7.2 są włączone ( ) lub wyłączone (`true`). Jeśli `true` `Switch.UseLegacyAccessibilityFeatures` , musi `true` być również, aby włączyć .NET Framework 4.7.1 funkcje ułatwień dostępu.| .NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Określa, czy funkcje ułatwień dostępu wprowadzone w systemie`false`.NET`true`Framework 4.8 są włączone ( ) lub wyłączone ( ). Jeśli `true` `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` i `true`musi być również .| .NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Określa, czy etykietki narzędzi są wyświetlane, gdy użytkownik najedzie kursorem myszy nad kontrolką WPF (`true`),`false`czy są one wyświetlane zarówno na fokusie klawiatury, jak i za pomocą klawisza skrótu klawiaturowego ( , zachowanie domyślne). W przypadku aplikacji działających w programie .NET Framework 4.8, ale przeznaczonych na poprzednie wersje `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`programu `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework, włączenie fokusu klawiatury i obsługi klawiszy skrótów wymaga, aby program , a wszystkie były ustawione na `false`.| .NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Określa, czy puste sekwencje kluczy w kluczach złożonych są ignorowane przez sprawdzanie poprawności schematu XSD. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Sprawdzanie poprawności schematu XML](../../../migration-guide/mitigation-xml-schema-validation.md).|Program .NET Framework 4.6|

> [!NOTE]
> Zamiast dodawać `AppContextSwitchOverrides` element do pliku konfiguracji aplikacji, można również ustawić przełączniki `static` programowo, wywołując `Shared` metodę (w <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> języku C#) lub (w języku Visual Basic).

 Deweloperzy bibliotek mogą również definiować niestandardowe przełączniki, aby umożliwić wywołującym rezygnację ze zmienionych funkcji wprowadzonych w nowszych wersjach ich bibliotek. Aby uzyskać więcej <xref:System.AppContext> informacji, zobacz klasę.

## <a name="switches-in-aspnet-applications"></a>Przełączniki w aplikacjach ASP.NET

Aplikację ASP.NET można skonfigurować do używania ustawień zgodności, dodając element [ \<Dodaj>](../appsettings/add-element-for-appsettings.md) do sekcji [ \<appSettings>](../appsettings/index.md) pliku web.config.

W poniższym przykładzie `<add>` użyto elementu `<appSettings>` do dodania dwóch ustawień do sekcji pliku web.config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Przykład

 W poniższym `AppContextSwitchOverrides` przykładzie użyto elementu do zdefiniowania `Switch.System.Globalization.NoAsyncCurrentCulture`przełącznika zgodności pojedynczej aplikacji, który zapobiega przepływaniu kultury przez wątki w wywołaniach metody asynchroniczne.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 W poniższym przykładzie `AppContextSwitchOverrides` użyto tego elementu do `Switch.System.Globalization.NoAsyncCurrentCulture` zdefiniowania dwóch przełączników zgodności aplikacji i `Switch.System.IO.BlockLongPaths`. Średnik oddziela dwie pary nazwy/wartości.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<element> środowiska uruchomieniowego](runtime-element.md)
- [\<element> konfiguracji](../configuration-element.md)
