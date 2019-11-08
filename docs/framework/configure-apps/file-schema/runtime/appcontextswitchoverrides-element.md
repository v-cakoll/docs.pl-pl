---
title: <AppContextSwitchOverrides> Element
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 881b9fedfaa42ffb402e226a6b271f47feb20617
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736813"
---
# <a name="appcontextswitchoverrides-element"></a>\<element > AppContextSwitchOverrides
Definiuje co najmniej jeden przełącznik używany przez klasę <xref:System.AppContext>, aby zapewnić mechanizm rezygnacji dla nowych funkcji.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<AppContextSwitchOverrides >**  
  
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
|"nazwa = wartość"|Wstępnie zdefiniowana nazwa przełącznika wraz z jej wartością (`true` lub `false`). Wiele par nazwa/wartość przełącznika jest oddzielonych średnikami (";"). Aby zapoznać się z listą wstępnie zdefiniowanych nazw przełączników obsługiwanych przez .NET Framework, zobacz sekcję Uwagi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od .NET Framework 4,6, element `<AppContextSwitchOverrides>` w pliku konfiguracji umożliwia wywoływania interfejsu API, aby określić, czy aplikacja może korzystać z nowych funkcji, czy zachować zgodność z poprzednimi wersjami biblioteki. Na przykład, jeśli zachowanie interfejsu API uległo zmianie między dwiema wersjami biblioteki, element `<AppContextSwitchOverrides>` umożliwia wywołujących tego interfejsu API, aby zrezygnować z nowego zachowania w wersjach biblioteki, które obsługują nową funkcję. W przypadku aplikacji, które wywołują interfejsy API w .NET Framework, element `<AppContextSwitchOverrides>` może również zezwalać wywołującym, których aplikacje są przeznaczone dla starszej wersji .NET Framework, aby zrezygnować z nowych funkcji, jeśli ich aplikacja działa w wersji .NET Framework, która obejmuje to zestaw.  
  
 Atrybut `value` elementu `<AppContextSwitchOverrides>` składa się z pojedynczego ciągu składającego się z jednej lub więcej par nazw/wartości rozdzielanych średnikami.  Każda nazwa identyfikuje przełącznik zgodności, a jego odpowiadająca wartość jest wartością logiczną (`true` lub `false`), która wskazuje, czy przełącznik jest ustawiony. Domyślnie przełącznik jest `false`, a biblioteki udostępniają nową funkcję. Zapewniają one tylko poprzednie funkcje, jeśli przełącznik jest ustawiony (to oznacza, że jego wartość jest `true`). Dzięki temu biblioteki mogą udostępniać nowe zachowanie dla istniejącego interfejsu API, jednocześnie umożliwiając wywoływanie, które zależą od poprzedniego zachowania, aby zrezygnować z nowych funkcji.  
  
 .NET Framework obsługuje następujące przełączniki:  
  
|Nazwa przełącznika|Opis|Wraca|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Kontroluje, czy Windows Presentation Foundation używa starszego algorytmu dla układu kontrolek. Aby uzyskać więcej informacji, zobacz [ograniczanie: układ WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Określa, czy domyślny algorytm używany do podpisywania części pakietu przez PackageDigitalSignatureManager jest SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Po ustawieniu na `false`, umożliwia debugowanie projektów przepływu pracy opartych na języku XAML z programem Visual Studio, gdy włączony jest standard FIPS. Bez niego <xref:System.NullReferenceException> jest generowany w wywołaniach metod w zestawie System. Activities.|.NET Framework 4,7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Określa, czy suma kontrolna wystąpienia przepływu pracy w debugerze używa algorytmu MD5 lub SHA1. | .NET Framework 4,7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Określa, czy mieszanie sum kontrolnych przepływu pracy używa algorytmu SHA1 wprowadzonego jako domyślny w .NET Framework 4,7 (`true`) lub czy używa domyślnego algorytmu SHA256 wprowadzonego jako domyślny w .NET Framework 4,8 (`false`).<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4,8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Kontroluje, czy ślady stosu uzyskują się, gdy użycie przenośnego plików PDB może obejmować plik źródłowy i informacje o wierszu. `false`, aby dołączyć plik źródłowy i informacje o wierszu; w przeciwnym razie `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Określa, czy metoda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> zgłasza wyjątek, gdy obiekt <xref:System.Drawing.Icon> ma ramki PNG. Aby uzyskać więcej informacji, zobacz [ograniczanie: ramki PNG w obiektach ikon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Określa, czy obiekty <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> są prawidłowo usuwane po dodaniu do kolekcji przez metodę <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>. `true` zachować starsze zachowanie; `false` do usuwania wszystkich prywatnych obiektów czcionek. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Określa, czy wydajność <xref:System.Windows.Forms.PrintPreviewDialog> jest zoptymalizowana pod kątem drukarek sieciowych. Aby uzyskać więcej informacji, zobacz [PrintPreviewDialog Control — Omówienie](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Określa, czy są wymuszane Sprawdzanie zakresu roku dla opcji wymazywania kalendarza japońskiego. `true`, aby wymusić sprawdzanie zakresu roku i `false` je wyłączyć (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Określa, czy tylko wartość "1" jest rozpoznawana jako pierwszy rok w ramach ery w przypadku kalendarza japońskiego podczas analizowania operacji. `true` rozpoznać tylko "1"; `false` rozpoznać wartości "1" lub Gannen (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Określa, czy pierwszy rok ery w kalendarzu japońskim jest reprezentowany jako "1" lub Gannen w operacjach formatowania. `true`, aby sformatować pierwszy rok era jako "1"; `false` sformatować go jako Gannen (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Określa, czy operacje asynchroniczne nie są przepływem z kontekstu wywołującego wątku. Aby uzyskać więcej informacji, zobacz [CurrentCulture i CurrentUICulture Flow dla zadań](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Określa, czy metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> próbuje dopasować typ zgłoszenia tylko do ostatniego wpisu DNS. Aby uzyskać więcej informacji, zobacz [Metoda ograniczania: X509CertificateClaimSet. FindClaims](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Określa, czy zezwolić AuthorizationContext. Empty na zwracanie modyfikowalnego obiektu.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Kontroluje, czy ścieżki dłuższe niż `MAX_PATH` (260 znaków) generują <xref:System.IO.PathTooLongException>. Aby uzyskać więcej informacji, zobacz [Obsługa długich ścieżek](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Kontroluje, czy natywne procedury systemu operacyjnego są używane do dekompresji przez klasę <xref:System.IO.Compression.DeflateStream>. `false` używać natywnych interfejsów API; `true` użyć implementacji <xref:System.IO.Compression.DeflateStream>.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Używa ukośnika odwrotnego ("\\"), a nie ukośnika ("/") jako separatora ścieżki we właściwości <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, [Zobacz FullName.](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Określa, czy wyjątki systemu operacyjnego, które są zgłaszane w wątkach w tle utworzonych przy użyciu <xref:System.IO.Ports.SerialPort> strumieni zakończą proces.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Kontroluje, czy jest używana normalizacja starszej ścieżki, a ścieżki URI są obsługiwane przez metody <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów: Normalizacja ścieżki](../../../migration-guide/mitigation-path-normalization.md) i [łagodzenie: sprawdzanie dwukropka Path](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Określa, czy test pod kątem równości porównuje Właściwość <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> jednego obiektu z właściwością <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> drugiego obiektu. Aby uzyskać więcej informacji, zobacz [niepoprawna implementacja MemberDescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Wyłącza sprawdzanie poprawności identyfikatora obiektu ulepszonego użycia klucza (EKU) certyfikatu. Rozszerzenie ulepszonego użycia klucza (EKU) to zbiór identyfikatorów obiektów (OID) wskazujący aplikacje, które używają klucza.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Wyłącza funkcję BEAST w przeglądarce TLS 1.0 przed ograniczeniami protokołu SSL/TLS, uniemożliwiając korzystanie z SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Określa, czy klasy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> mogą korzystać z protokołu SSL 3,0. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów: protokoły TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Wyłącza przywracanie wersji SystemDefault TLS z powrotem do domyślnej wartości Tls12, Tls11, TLS.|.NET Framework 4,7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Wyłącza alerty po stronie serwera SslStream TLS.|.NET Framework 4,7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Kontroluje, czy parametry ByRef SafeArray w zdarzeniach międzyoperacyjności modelu COM są przekazywane z powrotem do kodu natywnego (`false`) lub czy kierowanie do kodu natywnego jest wyłączone (`true`).|.NET Framework 4,8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Określa, czy [Klasa DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializować niektóre znaki kontrolne w oparciu o standardy ECMAScript V6 i V8. Aby uzyskać więcej informacji, zobacz [ograniczanie: serializacji znaków kontrolnych za pomocą Klasa DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4,7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Określa, czy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje wiele korekt, czy tylko pojedyncze dopasowanie dla strefy czasowej. Jeśli `true`, używa typu <xref:System.TimeZoneInfo> do serializacji i deserializacji danych daty i godziny. w przeciwnym razie używa typu <xref:System.TimeZone>, który nie obsługuje wielu reguł korekty.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Kontroluje, czy <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> zużywa większy rozmiar tablicy podczas serializacji obiektu i deserializacji. Ustaw ten przełącznik na `true`, aby zwiększyć wydajność serializacji i deserializacji grafów dużych obiektów według typów, takich jak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Określa, czy Konstruktor <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> ustawia właściwość <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> nowego obiektu z istniejącym odwołaniem do obiektu. Aby uzyskać więcej informacji, zobacz [ograniczanie: Identyfikator oświadczenia Konstruktor](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Określa, czy próba ponownego użycia <xref:System.Security.Cryptography.AesCryptoServiceProvider> deszyfrującego generuje <xref:System.Security.Cryptography.CryptographicException>. Aby uzyskać więcej informacji, zobacz [AesCryptoServiceProvider odszyfrowujący umożliwia przekształcenie wielokrotnego użytku](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Określa, czy wartość właściwości [CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) jest obiektem [IntPtr](xref:System.IntPtr) , który reprezentuje lokalizację pamięci uchwytu okna lub czy jest to uchwyt okna (HWND). Aby uzyskać więcej informacji, zobacz [ograniczanie: CspParameters. ParentWindowHandle oczekuje elementu HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4,7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Określa, czy używanie zarządzanych klas kryptograficznych w trybie FIPS zgłasza <xref:System.Security.Cryptography.CryptographicException> (`true`) lub opiera się na implementacji bibliotek systemowych (`false`).|.NET Framework 4,8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedCMS to SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Określa, czy metoda <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> prawidłowo obsługuje wszystkie nazwane krzywe obsługiwane przez system operacyjny (`false`) lub przywraca starsze zachowanie.|.NET Framework 4,8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedXML to SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Określa, czy tryb zabezpieczeń `TransportWithMessageCredential` zezwala na komunikaty z niepodpisanym nagłówkiem "do". Jest to przełącznik opcjonalny. Aby uzyskać więcej informacji, zobacz [zmiany w środowisku uruchomieniowym w .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Określa, czy Konstruktor <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> zgłasza <xref:System.ArgumentException>, jeśli jeden z elementów jest `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Określa, czy próba użycia certyfikatów x509 z dostawcą magazynu kluczy CSG zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|W przypadku korzystania z transportu HTTP z usługą samoobsługową ustawienie tej wartości na `true` powoduje ignorowanie przez program WCF aplikacji, która dodaje nagłówek `Connection: close` do nagłówków odpowiedzi dla żądania. Ustawienie tej wartości na `false` umożliwia dodanie nagłówka `Connection: close` do nagłówków odpowiedzi, co spowoduje zamknięcie gniazda żądania po wysłaniu odpowiedzi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Obsługuje zakleszczenie wynikające z ograniczenia wystąpień usługi współużytkowanej do pojedynczego wątku wykonywania w danym momencie.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Wraz z `Switch.System.Net.DontEnableSchUseStrongCrypto`określa, czy zabezpieczenia komunikatów WCF korzystają z protokołów TLS 1,1 i TLS 1,2.|.NET Framework 4,7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Wartość `false` ustawia domyślną konfigurację, aby umożliwić systemowi operacyjnemu wybór protokołu. Wartość `true` ustawia domyślnie najwyższy dostępny protokół. (Dostępne również w rozgałęzieniu obsługi wcześniejszych wersji platformy)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Określa, czy domyślny algorytm podpisywania komunikatów dla komunikatów usługi MSMQ w programie WCF to SHA1 lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Kontroluje, czy funkcja WCF używa skrótu SHA1 lub SHA256 do generowania losowych nazw dla nazwanych potoków.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Określa, czy zgłaszać [NullReferenceException](xref:System.NullReferenceException) , gdy komunikat o wyjątku ma wartość null.|.NET Framework 4,7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Określa, czy wyjątki zgłoszone podczas uruchamiania usługi są propagowane do obiektu wywołującego metody <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Kontroluje, czy wystąpienia <xref:System.Threading.Timer> korzystają z ulepszeń wydajności dla środowisk o dużej skali. Jeśli `true`, ulepszenia wydajności są włączone; Jeśli `false` (wartość domyślna), są one wyłączone.|.NET Framework 4,8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Określa, czy niektóre znaki kodowane w procentach, które były czasami zdekodowane, są teraz ciągle kodowane w lewo. W przypadku `true`są dekodowane; w przeciwnym razie `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Określa obsługę znaków dwukierunkowych Unicode w identyfikatorach URI. `true` je rozdzielić od identyfikatorów URI; `false` zachować i zakodować procentowo.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Określa, czy Windows Presentation Foundation stosuje stary algorytm (`true`) czy nowy algorytm (`false`) w obszarze przydzielanie miejsca do \*kolumn. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów: Alokacja miejsca na kontrolce siatki do gwiazdki-Columns](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4,7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Określa, czy selektor lub kontrolka karta zawsze aktualizuje wartość wybranej właściwości Value przed podniesieniem zdarzenia zmiany zaznaczenia.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Określa, czy renderowanie wyboru na podstawie modułu nie jest dostępne dla formantów <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox>, aby zapobiec zamknięte tekstu (`false`) lub czy tekst jest renderowany tylko w warstwie modułu definiowania układu (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Kontroluje, czy niestandardowe indeksatory IList są używane niepoprawnie (`false`) lub poprawnie (`true`) przez klasę <xref:System.Windows.Data.Binding?displayProperty=nameWithType>.|.NET Framework 4,8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Określa, czy zmiany DPI są wykonywane dla systemu (wartość `false`) czy na monitor (wartość `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Określa, czy ulepszenia zmiany rozmiarów kontrolek w <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType>, gdy WPF jest uruchamiany w trybie rozpoznawania dla poszczególnych monitorów, są wyłączone (`true`) lub włączone (`false`).|.NET Framework 4,8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Określa, czy Deweloper musi specjalnie obsługiwać akcję <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>, gdy jest obecny tekst kontrolki. `true` obsłużyć akcję <xref:System.Windows.Forms.DomainUpDown.UpButton>; `false`, aby akcje <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> były prawidłowo zsynchronizowane.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Zamiast kodu, który zezwala na niestandardową implementację <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> na bezpieczne filtrowanie komunikatów bez zgłaszania wyjątku w przypadku wywołania metody <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z niestandardowymi implementacjami IMessageFilter. PreFilterMessage](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Określa, czy właściwość <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> zwraca kontrolę źródła, gdy użytkownik otwiera menu z zagnieżdżonej kontrolki <xref:System.Windows.Forms.ToolStripMenuItem>. `true` zwrócić `null`, starsze zachowanie; `false` zwrócić kontroli źródła.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Określa, czy obsługa wywołania etykietki narzędzia jest wyłączona (`true`) czy włączona (`false`). Włączenie obsługi wywołania etykietki narzędzia wymaga także, `false`aby zostały wyłączone starsze funkcje ułatwień dostępu zdefiniowane przez `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`i `Switch.UseLegacyAccessibilityFeatures.3`.|.NET Framework 4,8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Określa, czy w aplikacjach WPF jest włączony opcjonalny stos dotykowy/pióra oparty na `WM_POINTER`. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z obsługą dotykową i piórem na podstawie wskaźnika](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4,7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Określa, czy domyślnym algorytmem wyznaczania wartości skrótu używanym w przypadku sum kontrolnych jest SHA256 (`false`) lub SHA1 (`true`).<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Kontroluje, czy jest zgłaszane starsze [NullReferenceException](xref:System.NullReferenceException) zamiast wyjątku, który dokładniej wskazuje przyczynę wyjątku (na przykład [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) lub [FileNotFoundException](xref:System.IO.FileNotFoundException). Jest ona przeznaczona do użycia przez kod, który zależy od obsługi [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4,7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Kontroluje, czy mieszanie sum kontrolnych plików XOML w projekcie przepływu pracy korzysta z algorytmu MD5 (`true`) lub czy używają algorytmu SHA256 wprowadzonego jako domyślny w .NET Framework 4,8.<br>Ze względu na kolizje problemów z algorytmem MD5 firma Microsoft zaleca SHA256.|.NET Framework 4,8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Kontroluje, czy mieszanie sum kontrolnych przez SqlTrackingService używa algorytmu MD5 (`true`) do buforowania ciągów lub czy używa algorytmu SHA256 wprowadzonego jako wartość domyślna w .NET Framework 4,8.<br>Ze względu na kolizje problemów z algorytmem MD5 firma Microsoft zaleca SHA256.|.NET Framework 4,8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Kontroluje, czy mieszanie sum kontrolnych przez środowisko uruchomieniowe przepływu pracy używa algorytmu MD5 (`true`) do buforowanych definicji przepływu pracy lub czy używa algorytmu SHA256 wprowadzonego jako domyślny w .NET Framework 4,8.<br>Ze względu na kolizje problemów z algorytmem MD5 firma Microsoft zaleca SHA256.|.NET Framework 4,8|
|`Switch.UseLegacyAccessibilityFeatures`|Kontroluje, czy funkcje ułatwień dostępu dostępne począwszy od .NET Framework 4.7.1 są włączone lub wyłączone. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Określa, czy funkcje ułatwień dostępu dostępne w .NET Framework 4.7.2 są włączone (`false`) czy wyłączone (`true`). Jeśli `true`, `Switch.UseLegacyAccessibilityFeatures` również muszą być `true`, aby .NET Framework włączyć funkcję ułatwień dostępu 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Określa, czy funkcje ułatwień dostępu wprowadzone w .NET Framework 4,8 są włączone (`false`) czy wyłączone (`true`). Jeśli `true`, `Switch.UseLegacyAccessibilityFeatures` i `Switch.UseLegacyAccessibilityFeatures.2` również muszą być `true`.|.NET Framework 4,8|
|`Switch.UseLegacyToolTipDisplay`|Określa, czy etykietki narzędzi są wyświetlane, gdy użytkownik przesuwa wskaźnik myszy nad kontrolką WPF (`true`) lub czy są wyświetlane zarówno na nacisk klawiatury, jak i za pomocą klawisza skrótu klawiaturowego (`false`, zachowanie domyślne). W przypadku aplikacji uruchamianych w .NET Framework 4,8, ale przeznaczonych dla wcześniejszych wersji .NET Framework, włączenie obsługi zarówno klawiatury, jak i klawisza skrótu wymaga, aby `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`i `Switch.UseLegacyAccessibilityFeatures.3` wszystkie były ustawione na `false`.|.NET Framework 4,8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Określa, czy puste sekwencje klawiszy w kluczach złożonych są ignorowane przez walidację schematu XSD. Aby uzyskać więcej informacji, zobacz [ograniczanie: sprawdzanie poprawności schematu XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
> Zamiast dodawać `AppContextSwitchOverrides` elementu do pliku konfiguracji aplikacji, można również ustawić przełączniki programowo poprzez wywołanie `static` (in C#) lub `Shared` (w Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.  
  
 Deweloperzy bibliotek mogą również definiować niestandardowe przełączniki, aby umożliwić wywołującym rezygnację ze zmienionych funkcji wprowadzonych w nowszych wersjach ich bibliotek. Aby uzyskać więcej informacji, zobacz Klasa <xref:System.AppContext>.  
  
## <a name="switches-in-aspnet-applications"></a>Przełączniki w aplikacjach ASP.NET

Aby użyć ustawień zgodności, można skonfigurować aplikację ASP.NET, dodając [\<dodać element >](../appsettings/add-element-for-appsettings.md) do sekcji [\<AppSettings >](../appsettings/index.md) pliku Web. config. 

Poniższy przykład używa elementu `<add>`, aby dodać dwa ustawienia do sekcji `<appSettings>` pliku Web. config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Przykład

 Poniższy przykład używa elementu `AppContextSwitchOverrides`, aby zdefiniować pojedynczy przełącznik zgodności aplikacji, `Switch.System.Globalization.NoAsyncCurrentCulture`, który uniemożliwia przepływanie kultury między wątkami w wywołaniach metod asynchronicznych.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 Poniższy przykład używa elementu `AppContextSwitchOverrides`, aby zdefiniować dwa przełączniki zgodności aplikacji, `Switch.System.Globalization.NoAsyncCurrentCulture` i `Switch.System.IO.BlockLongPaths`. Należy zauważyć, że średnik oddziela dwie pary nazwa/wartość.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppContext?displayProperty=nameWithType>
- [Element > środowiska uruchomieniowego \<](runtime-element.md)
- [\<> elementu konfiguracji](../configuration-element.md)
