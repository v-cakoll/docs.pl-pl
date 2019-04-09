---
title: <AppContextSwitchOverrides> Element
ms.custom: updateeachrelease
ms.date: 03/07/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bc4cd94d3acd37244e1d5b882612e4b1da91b90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136464"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> Element
Definiuje co najmniej jeden przełączniki posługują się <xref:System.AppContext> Aby klasa zapewniała mechanizm rezygnacji z nowych funkcji.  
  
 \<Konfiguracja >  
 \<runtime>  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`value`|Atrybut wymagany.<br /><br /> Definiuje co najmniej jedną nazwę przełącznika i ich skojarzone wartości logiczne.|  
  
### <a name="value-attribute"></a>wartość atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|"nazwa = wartość"|Nazwa przełącznika wstępnie zdefiniowany wraz z jego wartość (`true` lub `false`). Wiele pary nazwa/wartość przełącznika są oddzielone średnikami (";"). Aby uzyskać listę nazw wstępnie zdefiniowanych przełączników, obsługiwane przez program .NET Framework Zobacz sekcję Uwagi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu .NET Framework 4.6 `<AppContextSwitchOverrides>` elementu w pliku konfiguracji umożliwia wywołań interfejsu API, aby ustalić, czy jego aplikacja może korzystać z zalet nowych funkcji lub zachowania zgodności z poprzednimi wersjami biblioteki. Na przykład, jeśli zachowanie interfejsu API została zmieniona między dwoma wersjami biblioteki `<AppContextSwitchOverrides>` element pozwala obiektom wywołującym tego interfejsu API, aby zrezygnować z nowego zachowania na wersje biblioteki, które obsługują nowe funkcje. Dla aplikacji, które wywoływania interfejsów API na platformie .NET Framework `<AppContextSwitchOverrides>` element można również zezwolić wywoływania, w których aplikacje są przeznaczone dla starszej wersji programu .NET Framework, aby skorzystać z nowych funkcji, jeśli jego aplikacja jest uruchomiona na wersję .NET Framework, który zawiera funkcje.  
  
 `value` Atrybutu `<AppContextSwitchOverrides>` element składa się z pojedynczy ciąg, który składa się z jednego lub więcej par nazwa/wartość rozdzielaną średnikami.  Każda nazwa identyfikuje przełącznik zgodności, a jego wartość jest wartością logiczną (`true` lub `false`) oznacza to, czy przełącznik jest ustawiona. Domyślnie jest `false`, i udostępnia nowych funkcji w bibliotekach. Tylko zapewniają poprzednie funkcjonalności Jeśli przełącznik ma wartość (jego wartość jest `true`). Dzięki temu biblioteki, aby podać nowe zachowanie dla istniejących interfejsów API, zezwalając obiektów wywołujących, które zależą od poprzedniego zachowania, aby zrezygnować z nowych funkcji.  
  
 .NET Framework obsługuje następujące parametry:  
  
|Nazwa przełącznika|Opis|Wprowadzono|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Określa, czy Windows Presentation Foundation używa starszej wersji jest algorytm dla określania układu. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Układ platformy WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Określa, czy domyślny algorytm używany do podpisywania części pakietu przez PackageDigitalSignatureManager jest algorytm SHA1 lub SHA256.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Po ustawieniu `false`, umożliwia debugowanie projektów opartych na XAML przepływu pracy z programem Visual Studio, gdy Standard FIPS jest włączony. Bez tego <xref:System.NullReferenceException> jest zgłaszany w wywołaniach do metod w zestawie System.Activities.|.NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Określa, czy sumy kontrolnej dla wystąpienia przepływu pracy w debugerze, używa algorytmu MD5 lub SHA1. | .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Określa, czy mieszania sumy kontrolnej przepływ pracy używa algorytmu SHA1 wprowadzone jako domyślne w programie .NET Framework 4.7 (`true`), lub czy używa domyślny algorytm SHA256 wprowadzone jako domyślne w .NET Framework 4.8 (`false`).<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Określa, czy ślady stosu uzyskać przy użyciu przenośnych plików PDB może zawierać informacje o pliku i wierszu źródła. `false` Aby dołączyć pliku i wierszu informacji o źródle; w przeciwnym razie `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Formanty czy <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek podczas <xref:System.Drawing.Icon> obiekt ma ramek PNG. Aby uzyskać więcej informacji, zobacz [środki zaradcze: PNG ramki w obiektach ikonę](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Określa, czy <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> obiekty są prawidłowo usunięte, po dodaniu do kolekcji przy <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> metody. `true` Aby zachować starsze zachowanie; `false` do usuwania wszystkich obiektów prywatnej czcionki. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Formanty czy wydajność <xref:System.Windows.Forms.PrintPreviewDialog> została zoptymalizowana pod kątem drukarek sieciowych. Aby uzyskać więcej informacji, zobacz [printpreviewdialog — informacje o formancie](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Określa, czy zakres roku sprawdza, czy kalendarza japońskiego, które są wymuszane ery. `true` Aby wymusić zakresie roku sprawdza, i `false` można wyłączyć je (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Określa, czy tylko "1" jest rozpoznawany jako pierwszy rok ery kalendarza japońskiego, podczas operacji analizowania. `true` rozpoznawanie tylko "1"; `false` uznania "1" lub Gannen (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Określa, czy pierwszy rok ery kalendarza japońskiego jest reprezentowany jako "1" lub Gannen w operacjach formatowania. `true` Aby sformatować ery pierwszy rok jako "1"; `false` flagowana jako Gannen (zachowanie domyślne). Aby uzyskać więcej informacji, zobacz [Praca z kalendarzami](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Określa, czy operacje asynchroniczne nie przepływać z kontekstu wątku wywołującego. Aby uzyskać więcej informacji, zobacz [CurrentCulture i CurrentUICulture przepływać przez zadania](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Formanty czy <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować typ oświadczenia tylko w przypadku ostatni wpis DNS. Aby uzyskać więcej informacji, zobacz [środki zaradcze: X509CertificateClaimSet.FindClaims Method](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Określa, czy zezwalać na AuthorizationContext.Empty zwracać obiektu modyfikowalnego.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Formanty czy ścieżki dłuższe niż `MAX_PATH` throw (260 znaków) <xref:System.IO.PathTooLongException>. Aby uzyskać więcej informacji, zobacz [długa ścieżka pomocy technicznej](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Określa, czy macierzystym procedury systemu operacyjnego są używane do dekompresji przez <xref:System.IO.Compression.DeflateStream> klasy. `false` Aby użyć natywnych interfejsów API; `true` używać <xref:System.IO.Compression.DeflateStream> implementacji.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Używa ukośnik odwrotny ("\\") zamiast ukośnika ("/") jako separatora ścieżki w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji, zobacz [środki zaradcze: ZipArchiveEntry.FullName Path Separator](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Określa, czy wyjątki systemowe, które są generowane na wątkach w tle utworzonych za pomocą działania <xref:System.IO.Ports.SerialPort> strumieni zakończyć proces.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Określa, czy ścieżki starszych normalizacji jest używana i ścieżek identyfikatora URI są obsługiwane przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Ścieżka normalizacji](../../../migration-guide/mitigation-path-normalization.md) i [środki zaradcze: Ścieżka dwukropek kontroli](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Określa, czy test porównuje równość <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> właściwości jednego obiektu z <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> drugiego obiektu. Aby uzyskać więcej informacji, zobacz [nieprawidłowa implementacja MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Wyłącza certyfikatu weryfikacji identyfikatora (OID) obiektu rozszerzonego użycia klucza (EKU). Rozszerzenie rozszerzone użycie klucza (EKU) to zbiór identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Wyłącza środki zaradcze TLS1.0 przeglądarki wykorzystać przeciwko SSL/TLS (BEAST), wyłączając użytkowania SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Formanty czy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą używać protokołu SSL 3.0. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Protokoły TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Wyłącza wersje protokołu TLS SystemDefault powracanie do domyślnej Tls12, Tls11, Tls.|.NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Wyłącza alerty po stronie serwera SslStream TLS.|.NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Formanty czy [klasa DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje niektórych znaków kontrolnych opartych na standardach wersji ECMAScript 6 i V8. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Serializacja znaki kontrolne przy użyciu elementu DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Formanty czy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje wiele dostosowań lub tylko jednego dopasowania dla strefy czasowej. Jeśli `true`, używa ona <xref:System.TimeZoneInfo> typ do serializacji i deserializacji danych daty i godziny; w przeciwnym razie używa <xref:System.TimeZone> typ, który nie obsługuje wielu reguł dopasowania.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Formanty czy <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> większy rozmiar tablicy jest używany podczas obiektu serializacji i deserializacji. Ustaw ten przełącznik `true` do poprawy wydajności serializacji i deserializacji obiektu dużych wykresów obiektów według typów, takich jak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Formanty czy <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> Konstruktor Ustawia nowy obiekt <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> właściwość o istniejące odwołanie do obiektu. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Konstruktor ClaimsIdentity](../../../migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Formanty czy próba ponownego użycia <xref:System.Security.Cryptography.AesCryptoServiceProvider> zgłasza odszyfrowujący <xref:System.Security.Cryptography.CryptographicException>. Aby uzyskać więcej informacji, zobacz [odszyfrowujący AesCryptoServiceProvider zapewnia wielokrotnego użytku przekształcenie](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Formanty czy wartość [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) właściwość [IntPtr](xref:System.IntPtr) czy reprezentuje lokalizację w pamięci okna obsługi, lub czy jest to uchwyt okna (HWND). Aby uzyskać więcej informacji, zobacz [środki zaradcze: CspParameters.ParentWindowHandle oczekuje HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedCMS jest algorytm SHA1 lub SHA256.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedXML jest algorytm SHA1 lub SHA256.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Określa, czy `TransportWithMessageCredential` tryb zabezpieczeń umożliwia komunikatów za pomocą niepodpisany "nagłówek do". Jest to przełącznik zgłoszenie zgody na uczestnictwo. Aby uzyskać więcej informacji, zobacz [zmiany środowiska uruchomieniowego w programie .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Formanty czy <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Konstruktor wyrzuca <xref:System.ArgumentException> po spełnieniu jednego z elementów `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Określa, czy próbę użycia X509 certyfikatów przy użyciu dostawcy magazynu kluczy CSG zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [WCF transport security obsługuje certyfikaty przechowywane przy użyciu CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Korzystając z protokołu HTTP przy użyciu samodzielnie hostowanej usługi, ustawienie tej wartości na `true` powoduje, że usługi WCF do ignorowania dodawania aplikacji `Connection: close` nagłówka do nagłówków odpowiedzi na żądanie. Ustawienie tej wartości na `false` umożliwia dodawanie `Connection: close` nagłówka do nagłówków odpowiedzi, co powoduje zamknięcie gniazda żądania po wysłaniu odpowiedzi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Obsługuje zakleszczenia wynikających z ograniczenia wystąpień usługi współużytkowane do pojedynczego wątku wykonania w danym momencie.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Wraz z `Switch.System.Net.DontEnableSchUseStrongCrypto`, określa, czy zabezpieczenie wiadomości WCF używa protokołu TLS 1.1 i TLS 1.2.|.NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Wartość `false` ustawia domyślną konfigurację, aby system operacyjny wybrać protokół. Wartość `true` ustawiana domyślnie do protokołu najwyższy dostępny. (Ta funkcja jest dostępna również na gałąź z poprzednich wersji w ramach obsługi)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Określa, czy komunikat domyślny algorytm dla wiadomości usługi MSMQ w usłudze WCF podpisywania jest algorytm SHA1 lub SHA256.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Określa, czy WCF używa SHA1 lub skrót SHA256 do wygenerowania losowych nazw dla nazwanych potoków.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Określa, czy [obiektu NullReferenceException](xref:System.NullReferenceException) kiedy komunikat o wyjątku ma wartość null.|.NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Określa, czy wyjątki generowane podczas uruchamiania usługi są propagowane do obiektu wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET Framework 4.7.1|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Określa, czy niektóre zakodowane w formacie procent, które zostały czasami zdekodowany teraz spójnie lewej kodowania znaków. Jeśli `true`, są one zdekodowany; w przeciwnym razie `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Określa obsługi znaków dwukierunkowy Unicode w identyfikatorach URI. `true` Aby usunąć je z identyfikatorów URI; `false` zachowanie i procent zakodować je.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Określa, czy Windows Presentation Foundation mają zastosowanie stary algorytm (`true`) lub nowy algorytm (`false`) w przydzielanie miejsca, aby \*-kolumn. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Przydzielenie miejsca na formant siatki do kolumn Star](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Zdarzenie zmiany formanty czy selektora lub kartę sterowania zawsze aktualizuje wartość jego właściwości wybranej wartości przed zgłoszeniem zaznaczenia.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Określa, czy renderowanie na podstawie zaznaczenia — moduł definiowania układu dla <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> kontroli w celu zapobieżenia zamknięte tekstu (`false`), lub czy renderowania tekstu tylko w warstwie moduł definiowania układu kodu (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Określa, czy niestandardowe indeksatory IList używane są niepoprawnie (`false`) lub poprawnie (`true`) przez <xref:System.Windows.Data.Binding?displayProperty=nameWithtype> klasy.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Określa, czy wartość DPI zmianach w na systemie (wartość `false`) lub według poszczególnych monitorów (wartość `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Formanty czy poprawę rozmiaru formantów w <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> uruchamiania WPF w trybie pamiętać monitora są wyłączone (`true`) lub włączona (`false`).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Określa, czy deweloper musi obsługiwać specjalnie <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji, gdy tekst kontrolki jest obecna. `true` Aby obsłużyć <xref:System.Windows.Forms.DomainUpDown.UpButton> działania. `false` dla <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcji mają być prawidłowo synchronizowany.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Oznacza brak kod, który umożliwia niestandardowego zgody <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji bezpiecznie filtrować wiadomości bez zgłaszania wyjątku podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Określa, czy <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> właściwość zwraca kontroli źródła, gdy użytkownik otwiera menu z zagnieżdżoną <xref:System.Windows.Forms.ToolStripMenuItem> kontroli. `true` Aby zwrócić `null`, starsze zachowanie; `false` do zwrócenia do kontroli źródła.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Określa, czy obsługa wywołania etykietka narzędzia jest wyłączona (`true`) lub włączona (`false`). Włączanie obsługi wywołania etykietki narzędzia wymaga również starszych ułatwień dostępu zdefiniowane przez `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, i `Switch.UseLegacyAccessibilityFeatures.3` wszystkie wyłączone (wartość `false`).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Określa, czy jest to opcjonalne `WM_POINTER`— oparte na dotyku/pióro stosu jest włączona w aplikacjach WPF. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Oparte na wskaźnikach Dotyk i pomocy technicznej pióra](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Określa, czy domyślny algorytm skrótu używany do sumy kontrolne SHA256 (`false`) lub SHA1 (`true`).<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Określa, czy starszej [obiektu NullReferenceException](xref:System.NullReferenceException) jest generowany, a nie wyjątek, który wskazuje, w szczególności przyczyną wyjątku (takie jak [directorynotfoundexception —](xref:System.IO.DirectoryNotFoundException) lub [ FileNotFoundException](xref:System.IO.FileNotFoundException). Jest on przeznaczony do użytku przez kod, który zależy od obsługi [obiektu NullReferenceException](xref:System.NullReferenceException). | .NET framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Formanty czy sumy kontrolnej wyznaczania wartości skrótu z pliki XOML przepływu pracy projektu kompilacji należy używać algorytmu MD5 (`true`), czy używać algorytm SHA256 wprowadzone jako domyślne w .NET Framework 4.8.<br>Ze względu na problemy kolizji z MD5 firma Microsoft zaleca SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Określa, czy suma kontrolna wyznaczania wartości skrótu przy użyciu usługi SqlTrackingService używa algorytmu MD5 (`true`) dla pamięci podręcznej ciągów i czy używa wprowadzone jako domyślne w .NET Framework 4.8 algorytm SHA256.<br>Ze względu na problemy kolizji z MD5 firma Microsoft zaleca SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Określa, czy suma kontrolna wyznaczania wartości skrótu przez środowisko wykonawcze przepływów pracy używa algorytmu MD5 (`true`) dla definicji przepływu pracy w pamięci podręcznej i czy używa wprowadzone jako domyślne w .NET Framework 4.8 algorytm SHA256.<br>Ze względu na problemy kolizji z MD5 firma Microsoft zaleca SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Formanty dostępne począwszy od .NET Framework 4.7.1 funkcje ułatwień dostępu są włączone czy wyłączone. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Formanty, czy funkcje są dostępne w programie .NET Framework 4.7.2 ułatwień dostępu są włączane (`false`) lub wyłączony (`true`). Jeśli `true`, `Switch.UseLegacyAccessibilityFeatures` musi być także `true` Aby włączyć funkcje ułatwień dostępu w programie .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Formanty, czy funkcje ułatwień dostępu wprowadzone w .NET Framework 4.8 są włączone (`false`) lub wyłączony (`true`). Jeśli `true`, `Switch.UseLegacyAccessibilityFeatures` i `Switch.UseLegacyAccessibilityFeatures.2` musi być także `true`.|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Formanty czy etykietki narzędzi są displaed, gdy użytkownik ustawi wskaźnik myszy nad formantem WPF (`true`), lub czy są wyświetlane zarówno na klawiaturę, jak i za pośrednictwem klawisz skrótu (`false`, domyślne zachowanie). Dla aplikacji uruchomionych na .NET Framework 4,8, ale przeznaczone dla poprzednich wersji programu .NET Framework, jednocześnie umożliwiając klawiatury fokus i Obsługa kluczy skrótów wymaga `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, i `Switch.UseLegacyAccessibilityFeatures.3` można ustawić `false`.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Określa, czy pusta sekwencja klucza w klucze złożone są ignorowane przez sprawdzanie poprawności schematu XSD. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Sprawdzanie poprawności schematu XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Zamiast opcji dodawania `AppContextSwitchOverrides` elementu do pliku konfiguracji aplikacji, można również ustawić przełączników programowo przez wywołanie metody `static` (w języku C#) lub `Shared` (w języku Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.  
  
 Biblioteka deweloperzy mogą również definiować niestandardowe przełączników, aby umożliwić wywołującym zrezygnować z zmienione funkcje wprowadzone w nowszych bibliotek. Aby uzyskać więcej informacji, zobacz <xref:System.AppContext> klasy.  
  
## <a name="switches-in-aspnet-applications"></a>Przełączniki w aplikacjach ASP.NET

Można skonfigurować aplikację ASP.NET, aby użyć ustawień zgodności, dodając [ \<Dodaj >](../../../configure-apps/file-schema/appsettings/add-element-for-appsettings.md) elementu [ \<appSettings >](../../../configure-apps/file-schema/appsettings/index.md) sekcja pliku web.config. 

W poniższym przykładzie użyto `<add>` elementu do dodania dwóch ustawień `<appSettings>` sekcja pliku web.config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Przykład

 W poniższym przykładzie użyto `AppContextSwitchOverrides` elementu, aby zdefiniować przełącznikiem zgodność z pojedynczą aplikacją `Switch.System.Globalization.NoAsyncCurrentCulture`, który uniemożliwia przechodzącym przez wątki w wywołaniach metody asynchronicznej przez kulturę.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 W poniższym przykładzie użyto `AppContextSwitchOverrides` elementu, aby zdefiniować dwa przełączniki zgodności aplikacji `Switch.System.Globalization.NoAsyncCurrentCulture` i `Switch.System.IO.BlockLongPaths`. Należy pamiętać, że średnik oddziela dwie pary nazwa/wartość.  
  
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
- [\<środowisko uruchomieniowe > Element](runtime-element.md)
- [\<Konfiguracja > Element](../configuration-element.md)
