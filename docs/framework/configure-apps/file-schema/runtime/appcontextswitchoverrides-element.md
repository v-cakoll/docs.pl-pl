---
title: "&lt;AppContextSwitchOverrides&gt; — Element"
ms.custom: 
ms.date: 10/17/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83244e1df239110d86367423b91458aefb5d07a5
ms.sourcegitcommit: 5bfcb8d341239df251351f318038d31cdc9159d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; — Element
Definiuje co najmniej jeden przełącznik używany przez <xref:System.AppContext> klasy, aby zapewnić mechanizm rezygnacji z nowych funkcji.  
  
 \<Konfiguracja >  
 \<Runtime >  
\<AppContextSwitchOverrides >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`value`|Atrybut wymagany.<br /><br /> Definiuje co najmniej jedną nazwę przełącznika oraz powiązanych wartości, wartość logiczna.|  
  
### <a name="value-attribute"></a>wartość atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|"nazwa = wartość"|Nazwa przełącznika wstępnie zdefiniowany wraz z jego wartość (`true` lub `false`). Wiele par nazw i wartości przełącznika są oddzielone średnikami (";"). Listę nazw wstępnie zdefiniowanych przełącznika obsługiwane przez program .NET Framework znajduje się w sekcji uwag.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 W programie .NET Framework 4.6 `<AppContextSwitchOverrides>` element w pliku konfiguracji umożliwia wywołań interfejsu API, aby ustalić, czy ich aplikacji mogą korzystać z nowych funkcji lub zachowania zgodności z poprzednimi wersjami biblioteki. Jeśli działanie interfejsu API została zmieniona między dwoma wersjami biblioteki, na przykład `<AppContextSwitchOverrides>` element umożliwia obiektom wywołującym tego interfejsu API, aby zrezygnować z nowe zachowanie w wersjach biblioteki, które obsługują nowe funkcje. W przypadku aplikacji, które wywoływania interfejsów API w programie .NET Framework `<AppContextSwitchOverrides>` elementu można także umożliwić wywołującym których aplikacje kątem starszej wersji programu .NET Framework do uczestnictwa w nowych funkcji, jeśli ich aplikacja działa w wersji systemu .NET Framework, która obejmuje, który funkcje.  
  
 `value` Atrybutu `<AppContextSwitchOverrides>` element składa się z jednego ciągu, która składa się z co najmniej jeden pary nazwa/wartość rozdzielaną średnikami.  Każda nazwa identyfikuje przełącznika zgodności, a jego wartość jest wartością logiczną (`true` lub `false`) wskazująca, czy przełącznik jest ustawiony. Domyślnie jest `false`, i udostępnia nowych funkcji w bibliotekach. Tylko zapewniają funkcje poprzednich Jeśli jest ustawiona przełącznik (to znaczy, że jego wartość wynosi `true`). Dzięki temu biblioteki, aby podać nowe zachowanie dla istniejącego interfejsu API, umożliwiając wywołań, które są zależne od poprzedniego zachowanie rezygnacji z nowych funkcji.  
  
 .NET Framework obsługuje następujące parametry:  
  
|Nazwa przełącznika|Opis|Wprowadzono|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Określa, czy program Windows Presentation Foundation używa starszego algorytmu układ formantu. Aby uzyskać więcej informacji, zobacz [ograniczenie: układ platformy WPF](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Określa, czy domyślny algorytm używany do podpisywania części pakietu przez PackageDigitalSignatureManager jest SHA1 lub SHA256.|.NET framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Jeśli wartość `false`, pozwala na debugowanie projektów opartych na języku XAML przepływu pracy z programem Visual Studio, gdy FIPS jest włączone. Bez tego <xref:System.NullReferenceException> jest zgłaszany w wywołaniach metody w zestawie elementu System.Activities.|.NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Określa, czy sumy kontrolnej dla wystąpienia przepływu pracy w debugerze używa MD5 lub SHA1. | .NET framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Formanty czy <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłosi wyjątek podczas <xref:System.Drawing.Icon> obiekt ma ramki PNG. Aby uzyskać więcej informacji, zobacz [środki zaradcze: PNG ramki w obiektach ikona](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Określa, czy operacje asynchroniczne nie przepływać z kontekstu wywołania wątku. Aby uzyskać więcej informacji, zobacz [CurrentCulture i CurrentUICulture przepływ między zadania](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Formanty czy <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować typ oświadczenia tylko w przypadku ostatni wpis DNS. Aby uzyskać więcej informacji, zobacz [środki zaradcze: metoda X509CertificateClaimSet.FindClaims](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.BlockLongPaths`|Formanty czy ścieżki przekracza `MAX_PATH` throw (260 znaków) <xref:System.IO.PathTooLongException>. Aby uzyskać więcej informacji, zobacz [długa ścieżka pomocy technicznej](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Używa kreska ułamkowa odwrócona ("\\") zamiast ukośnika ("/") jako separatora ścieżki w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji, zobacz [środki zaradcze: separatora ścieżki ZipArchiveEntry.FullName](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Określa, czy działania systemu wyjątki, które są generowane na wątki w tle utworzonych za pomocą <xref:System.IO.Ports.SerialPort> strumieni zakończenie procesu.|.NET framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Określa, czy normalizacji starszych ścieżka jest używana i ścieżki identyfikatora URI są obsługiwane przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [środki zaradcze: ścieżka normalizacji](~/docs/framework/migration-guide/mitigation-path-normalization.md) i [środki zaradcze: sprawdza dwukropek ścieżki](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Określa, czy test porównuje równość <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> właściwości jeden obiekt z <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> drugiego obiektu. Aby uzyskać więcej informacji, zobacz [niepoprawna implementacja MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Wyłącza certyfikatu weryfikacji identyfikator (OID) obiektu ulepszonego użycia klucza (EKU). Rozszerzenie rozszerzone użycie klucza (EKU) jest zbiorem identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Wyłącza ograniczenie TLS1.0 przeglądarki wykorzystać przeciwko SSL/TLS (BEAST) przez wyłączenie użycia SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Formanty czy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą używać protokołu SSL 3.0. Aby uzyskać więcej informacji, zobacz [ograniczenie: protokoły TLS](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Wyłącza wersji protokołu TLS SystemDefault powrót do domyślnego Tls12, Tls11, Tls.|.NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Powoduje wyłączenie protokołu TLS SslStream alerty po stronie serwera.|.NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Formanty czy [klasa DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje niektóre znaki kontrolne oparte na standardach wersja języka ECMAScript 6 i V8. Aby uzyskać więcej informacji, zobacz [środki zaradcze: serializacja znaki kontrolne z elementu DataContractJsonSerializer](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET framework 4.7 |
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Formanty czy <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> Konstruktor Ustawia nowy obiekt <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> właściwości z istniejącej odwołania do obiektu. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Konstruktor ClaimsIdentity](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Formanty czy próba ponownego użycia <xref:System.Security.Cryptography.AesCryptoServiceProvider> zgłasza odszyfrowujący <xref:System.Security.Cryptography.CryptographicException>. Aby uzyskać więcej informacji zobacz odszyfrowujący AesCryptoServiceProvider zapewnia transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform) wielokrotnego użytku.|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Formanty czy wartość [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) właściwość jest [IntPtr](xref:System.IntPtr) czy reprezentuje lokalizacji pamięci okna obsługi, lub czy jest uchwyt okna (HWND). Aby uzyskać więcej informacji, zobacz [środki zaradcze: CspParameters.ParentWindowHandle oczekuje HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |.NET framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedCMS jest SHA1 lub SHA256. |.NET framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedXML jest SHA1 lub SHA256. |.NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Określa, czy `TransportWithMessageCredential` tryb zabezpieczeń umożliwia wiadomości z niepodpisany "nagłówek do". Jest to przełącznik opcjonalnych. Aby uzyskać więcej informacji, zobacz [zmiany środowiska uruchomieniowego w programie .NET Framework 4.6.1](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Formanty czy <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> zgłasza konstruktora <xref:System.ArgumentException> po spełnieniu jednego z elementów `null`.|.NET framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Określa, czy certyfikaty próbę użycia X509 z dostawcy magazynu kluczy CSG zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [zabezpieczeń transportu WCF obsługuje certyfikaty przechowywane przy użyciu CNG](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Obsługuje zakleszczenie wynikających z ograniczenia wystąpień usługi współużytkowane do pojedynczego wątku wykonania naraz.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Wraz z programem `Switch.System.Net.DontEnableSchUseStrongCrypto`, określa, czy zabezpieczenia wiadomości WCF używa protokołu TLS 1.1 i TLS 1.2.|.NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Określa, czy komunikat domyślny algorytm wiadomości usługi MSMQ w programie WCF podpisywania jest algorytm SHA1 lub SHA256.|.NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Określa, czy WCF używa SHA1 lub skrót SHA256 w celu generowania losowego nazw dla nazwanych potoków.|.NET framework 4.7.1|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Określa, czy wyjątki zgłaszane podczas uruchamiania usługi są propagowane do wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET framework 4.7.1|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Określa, czy Windows Presentation Foundation stosuje algorytm stary (`true`) lub nowego algorytmu (`false`) w przydzielania miejsca, aby \*-kolumn. Aby uzyskać więcej informacji, zobacz [środki zaradcze: przydzielenie miejsca na formancie siatki kolumnom gwiazdkę](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |.NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Formanty czy selektora lub kartę formant zawsze aktualizuje wartość jego właściwości wybranej wartości przed zgłoszeniem zaznaczenie zdarzenia zmiany.|.NET framework 4.7.1|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Wyłącza funkcję kod, który umożliwia niestandardowego <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji, aby bezpiecznie filtrować wiadomości bez generowania wyjątku podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana. Aby uzyskać więcej informacji, zobacz [środki zaradcze: implementacje IMessageFilter.PreFilterMessage niestandardowy](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Określa, czy jest to opcjonalny `WM_POINTER`— na podstawie touch/pióro stosu jest włączona w aplikacji WPF. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Touch oparte na wskaźnik i pomocy technicznej pióra](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Określa, czy starsze [NullReferenceException](xref:System.NullReferenceException) jest generowany, zamiast wyjątek, który wskazuje, w szczególności przyczyną wyjątku (takich jak [directorynotfoundexception —](xref:System.IO.DirectoryNotFoundException) lub [ FileNotFoundException](xref:System.IO.FileNotFoundException). Jest on przeznaczony do użytku przez kod, który jest zależny od obsługi [NullReferenceException](xref:System.NullReferenceException). | .NET framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|Formanty czy dostępnych w programie .NET Framework 4.7.1 funkcje ułatwień dostępu są włączone lub wyłączone. | .NET framework 4.7.1 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Określa, czy puste sekwencje klucza w klucze złożone są ignorowane przez Weryfikacja schematu XSD. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Sprawdzanie poprawności schematu XML](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Zamiast opcji dodawania `AppContextSwitchOverrides` elementu do pliku konfiguracji aplikacji, można również ustawić przełączników programowo przez wywołanie metody `static` (w języku C#) lub `Shared` (w języku Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.  
  
 Deweloperzy biblioteki również możliwość definiowania niestandardowych przełączników, aby umożliwić wywołującym rezygnacji z zmienione funkcje wprowadzone w nowszych wersjach ich bibliotek. Aby uzyskać więcej informacji, zobacz <xref:System.AppContext> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `AppContextSwitchOverrides` elementu, aby zdefiniować przełącznikiem zgodności pojedynczej aplikacji `Switch.System.Globalization.NoAsyncCurrentCulture`, który uniemożliwia kultury w drodze pomiędzy wątkami w wywołań metod asynchronicznych.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 W poniższym przykładzie użyto `AppContextSwitchOverrides` element, aby zdefiniować dwa przełączniki zgodności aplikacji, `Switch.System.Globalization.NoAsyncCurrentCulture` i `Switch.System.IO.BlockLongPaths`. Należy pamiętać, że średnikiem oddziela dwa pary nazwa/wartość.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppContext?displayProperty=nameWithType>  
 [\<środowisko uruchomieniowe > — Element](runtime-element.md)  
 [\<Konfiguracja > — Element](../configuration-element.md)
