---
title: "Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f2ef91986cb5ad31560c4a7f418218a168f1b2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)
Narzędzie metadanych elementu ServiceModel narzędzie jest używane do generowania kodu modelu usługi z dokumentów metadanych i dokumentów metadanych z kodu modelu usługi.  
  
## <a name="svcutilexe"></a>SvcUtil.exe  
 Narzędzie narzędzia metadanych elementu ServiceModel znajduje się w lokalizacji instalacji zestawu Windows SDK, w szczególności C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin  
  
### <a name="functionalities"></a>Funkcje  
 W poniższej tabeli przedstawiono różne funkcje udostępniane przez to narzędzie, a odpowiedni temat, który opisano, jak będą wykorzystywane.  
  
|Zadanie|Temat|  
|----------|-----------|  
|Generuje kod z systemem usług lub dokumentów metadanych statycznych.|[Generowanie klienta programu WCF na podstawie metadanych usługi](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|  
|Eksportuje dokumentów metadanych ze skompilowanego kodu.|[Porady: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|  
|Weryfikuje skompilowanego kodu usługi.|[Porady: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|  
|Pobiera dokumentów metadanych z uruchomionymi usługami.|[Porady: używanie Svcutil.exe do pobierania dokumentów metadanych](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|  
|Generuje kod serializacji.|[Porady: poprawy uruchamiania czasu programu WCF aplikacje klienckie przy użyciu elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|  
  
> [!CAUTION]
>  Narzędzia svcutil spowoduje zastąpienie istniejących plików na dysku, jeśli nazwy podana jako parametry są identyczne. Mogą to być pliki kodu, konfiguracji lub pliki metadanych. Aby tego uniknąć podczas generowania kodu i konfigurację prostej, użyj `/mergeConfig` przełącznika.  
>   
>  Ponadto `/r` i `/ct` przełączniki odwoływanie do typów są generowania kontraktów danych. Te przełączniki nie działają w przypadku przy użyciu elementu XmlSerializer.  
  
### <a name="timeout"></a>Limit czasu  
 Narzędzie ma 5 minut przekroczenie limitu czasu podczas pobierania metadanych.  Ten limit ma zastosowanie tylko do pobierania metadanych za pośrednictwem sieci. Nie ma zastosowania do jakiegokolwiek przetwarzania tych metadanych.  
  
### <a name="multi-targetting"></a>Profilowanie wielu grup  
 Narzędzie nie obsługuje wielowersyjności kodu. Jeśli chcesz wygenerować artefaktu .NET 4 z svcutil.exe, należy użyć svcutil.exe z zestawu SDK .NET 4. Aby wygenerować artefaktu .NET 3.5, użyj pliku wykonywalnego z zestawu SDK .NET 3.5.  
  
### <a name="accessing-wsdl-documents"></a>Uzyskiwanie dostępu do dokumentów WSDL  
 Gdy używasz narzędzia Svcutil dokument WSDL, który odwołuje się do usługi tokenu zabezpieczającego (STS) dostęp do narzędzia Svcutil sprawia, że WS-MetadataExchange, wywołanie usługi STS. Jednak usługa mogą uwidaczniać jej dokumentów WSDL przy użyciu protokołu WS-MetadataExchange lub HTTP GET. W związku z tym jeśli usługi STS jest dostępne tylko dokument WSDL przy użyciu HTTP GET klienta zapisany [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] zakończy się niepowodzeniem. Dla klientów w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], Svcutil podejmie próbę użycia obu WS-MetadataExchange i HTTP GET w celu uzyskania STS WSDL.  
  
## <a name="using-svcutilexe"></a>Przy użyciu SvcUtil.exe  
  
### <a name="common-usages"></a>Typowe zastosowania  
 W poniższej tabeli przedstawiono niektóre najczęściej używanych opcji dla tego narzędzia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|/ directory:\<katalogu >|Katalog, aby utworzyć pliki w.<br /><br /> Wartość domyślna: Bieżącego katalogu.<br /><br /> Krótka forma:`/d`|  
|/help|Wyświetla składnię polecenia i opcje narzędzia.<br /><br /> Krótka forma:`/?`|  
|/ nologo|Pomiń komunikat o prawach autorskich oraz transparent.|  
|/svcutilConfig:\<configFile >|Określa plik konfiguracji niestandardowej do użycia zamiast pliku App.config. Może być używany do zarejestrowania rozszerzenia system.serviceModel bez modyfikacji pliku konfiguracji narzędzia.|  
|/ target:\<typu output >|Określa wyjściowy, który ma być generowany przez narzędzie.<br /><br /> Prawidłowe wartości to kodu, metadane i xmlSerializer.<br /><br /> Krótka forma:`/t`|  
  
### <a name="code-generation"></a>Generowanie kodu  
 Svcutil.exe można wygenerować kodu dla usługi kontrakty, klientów i typy danych z dokumentów metadanych. Te dokumenty metadane mogą znajdować się na trwałe magazynu lub pobierana w trybie online. Pobieranie online następuje protokołu WS-Metadata Exchange lub protokołu DISCO (szczegółowe informacje można znaleźć w sekcji pobierania metadanych).  
  
 Można użyć narzędzia SvcUtil.exe do generowania kontraktów usług i danych na podstawie wstępnie zdefiniowanej dokumentu WSDL. Użyj przełącznika /serviceContract i określ lokalizację pliku lub adres URL, którym dokument WSDL, można pobrać lub znaleziono. Spowoduje to wygenerowanie kontraktów usług i danych, zdefiniowana w dokumencie WSDL, który następnie może służyć do implementacji usługi zgodne. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Porady: Pobieranie metadanych i implementacji usługi zgodne](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).  
  
 Usługi z punktem końcowym obiekt BasicHttpContextbinding Svcutil.exe generuje BasicHttpBinding z `allowCookies` ustawić atrybutu `true` zamiast tego. Pliki cookie są używane dla kontekstu na serwerze. Jeśli chcesz zarządzać kontekstu na kliencie, gdy usługa używa plików cookie, można ręcznie zmodyfikować konfigurację, aby użyć kontekstu powiązania.  
  
> [!CAUTION]
>  Svcutil.exe generuje klienta na podstawie pliku WSDL lub zasady, otrzymał od usługi. Główna nazwa użytkownika (UPN) jest generowana przez połączenie nazwy użytkownika, "@" i w pełni kwalifikowaną nazwą domeny (FQDN). Jednak dla użytkowników, którzy zarejestrowane w usłudze Active Directory, ten format jest nieprawidłowy i UPN wygenerowany przez narzędzie powoduje to niepowodzenie w uwierzytelnianiu Kerberos z komunikatem o błędzie "Próba logowania nie powiodła się". Aby rozwiązać ten problem, należy ręcznie naprawić plik klienta generowanego przez to narzędzie.  
  
 `svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`  
  
|Argument|Opis|  
|--------------|-----------------|  
|`epr`|Ścieżka do pliku XML, który zawiera WS-Addressing EndpointReference punktu końcowego usługi, która obsługuje WS-Metadata Exchange. Aby uzyskać więcej informacji zobacz sekcję pobierania metadanych.|  
|`metadataDocumentPath`|Ścieżka dokumentu metadanych (wsdl lub xsd), który zawiera kontrakt można zaimportować do kodu (.wsdl, XSD, .wspolicy lub .wsmex).<br /><br /> Narzędzia svcutil następuje importów i zawiera w przypadku określenia zdalnego adresu URL metadanych. Jednak jeśli użytkownik chce przetwarzać pliki metadanych w lokalnym systemie plików, należy określić wszystkie pliki w tego argumentu. W ten sposób można użyć narzędzia Svcutil w środowisku kompilacji gdzie nie może mieć zależności sieci. Można używać symboli wieloznacznych (*.xsd, \*.wsdl) dla tego argumentu.|  
|`url`|Adres URL punktu końcowego usługi, która udostępnia metadane lub dokument metadanych, hostowana w trybie online. Aby uzyskać więcej informacji, w jaki sposób te dokumenty są pobierane zobacz sekcję pobierania metadanych.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|/Async|Generuje zarówno podpisy metod synchroniczne i asynchroniczne.<br /><br /> Wartość domyślna: generowanie tylko metoda synchroniczna podpisów.<br /><br /> Krótka forma:`/a`|  
|/collectionType:\<typu >|Określa typ kolekcji listy dla klienta programu WCF.<br/><br /> Wartość domyślna: typ kolekcji jest System.Array. <br /><br /> Krótka forma:`/ct`|  
|/ config:\<configFile >|Określa nazwę pliku dla pliku konfiguracji wygenerowany.<br /><br /> Domyślne: output.config|  
|/dataContractOnly|Generuje kod dla tylko typy kontraktu danych. Nie zostały wygenerowane typy kontraktu usługi.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka forma:`/dconly`|  
|/enableDataBinding|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu na wszystkich typach kontraktu danych, aby umożliwić wiązanie danych.<br /><br /> Krótka forma:`/edb`|  
|/excludeType:\<typu >|Określa nazwę typu w pełni kwalifikowaną lub kwalifikowaną dla zestawu mają być wykluczone z typów, do którego istnieje odwołanie kontraktu.<br /><br /> Korzystając z tego przełącznika razem z `/r` z oddzielnych bibliotek DLL, odwołuje się pełna nazwa klasy XSD.<br /><br /> Krótka forma:`/et`|  
|/importXmlTypes|Konfiguruje serializator kontraktu danych do importowania typów kontraktu danych jako typów IXmlSerializable.|  
|/ wewnętrzny|Generuje klasy, które są oznaczone jako wewnętrzne. Wartość domyślna: generowanie tylko klas publicznych.<br /><br /> Krótka forma:`/i`|  
|/Language:\<języka >|Określa język programowania do użycia podczas generowania kodu. Należy podać nazwę języka zarejestrowanego w pliku Machine.config lub pełni kwalifikowaną nazwę klasy, która dziedziczy po <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Wartości: c#, cs, csharp, vb, języka Visual Basic, c ++, cpp<br /><br /> Domyślne: csharp<br /><br /> Skrócona forma: `/l` **Uwaga:** Przełącznik obsługuje tylko C++ dostawcy kodu, który jest dostarczany z programu Visual Studio 2005 z dodatkiem SP1.|  
|/mergeConfig|Scala istniejący plik, zamiast zastępowanie istniejącego pliku wygenerowanego konfiguracji.|  
|/messageContract|Generuje typy kontraktu komunikatu.<br /><br /> Krótka forma:`/mc`|  
|/ NAMESPACE:\<ciąg, ciąg >|Określa mapowania z targetNamespace WSDL lub schematu XML na przestrzeń nazw środowiska CLR. Za pomocą "\*" dla przestrzeń nazw targetNamespace mapuje wszystkie targetNamespaces bez jawnego mapowania do tej przestrzeni nazw CLR.<br /><br /> Aby upewnić się, że nazwa kontraktu komunikatu nie kolidujący z nazwy operacji, należy albo kwalifikujesz się odwołanie do typu z `::`, lub upewnij się, że nazwy są unikatowe.<br /><br /> Wartość domyślna: Obliczane na podstawie docelowego obszaru nazw dokumentu schematu dla kontraktów danych. Domyślna przestrzeń nazw jest używana dla wszystkich innych typów wygenerowany.<br /><br /> Krótka forma: `/n` **Uwaga:** podczas generowania typów do użycia z XmlSerializer, jest obsługiwana tylko jedna przestrzeń nazw mapowania. Wszystkie typy wygenerowane będzie w domyślnej przestrzeni nazw lub przestrzeni nazw określonej przez "*".|  
|/ noconfig|Generuje pliki konfiguracji.|  
|/ nostdlib|Nie odwołuj się do bibliotek standardowych.<br /><br /> Wartość domyślna: Odwołuje się Mscorlib.dll i System.servicemodel.dll.|  
|/ out:\<pliku >|Określa nazwę pliku dla wygenerowanego kodu.<br /><br /> Wartość domyślna: Na podstawie nazwy definicji WSDL, WSDL nazwy usługi lub docelowego obszaru nazw jednego ze schematów.<br /><br /> Krótka forma:`/o`|  
|/ reference:\<ścieżka pliku >|Typy odwołań w określonym zestawie. Podczas generowania klientów, ta opcja umożliwia Określ zestawy, które może zawierać typy, które reprezentują importowane metadane.<br /><br /> Nie można określić kontraktów komunikatu i <xref:System.Xml.Serialization.XmlSerializer> typów, za pomocą tego przełącznika.<br /><br /> Jeśli <xref:System.DateTimeOffset> odwołać się do tego typu jest używana zamiast funkcji generowania nowego typu. Jeśli aplikacja jest zapisywany przy użyciu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], odwołania SvcUtil.exe <xref:System.DateTimeOffset> automatycznie.<br /><br /> Krótka forma:`/r`|  
|/ możliwy do serializacji|Generuje klasy oznaczonej przez atrybut możliwy do serializacji.<br /><br /> Krótka forma:`/s`|  
|/serviceContract|Generuj kod dla tylko kontraktów usług. Klasa klienta i konfiguracji nie zostanie wygenerowany<br /><br /> Krótka forma:`/sc`|  
|/serializer:Auto|Automatyczne wybieranie serializatora. Próbuje użyć serializator kontraktu danych i używa XmlSerializer, jeśli się nie powiedzie.<br /><br /> Krótka forma:`/ser`|  
|/serializer:dataContractSerializer|Generuje typy danych, które używają do serializacji i deserializacji serializator kontraktu danych.<br /><br /> Krótka forma:`/ser:DataContractSerializer`|  
|/serializer:XmlSerializer|Generuje typów danych, które używają <xref:System.Xml.Serialization.XmlSerializer> do serializacji i deserializacji.<br /><br /> Krótka forma:`/ser:XmlSerializer`|  
|/targetClientVersion|Określ wersję [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] jest element docelowy aplikacji. Prawidłowe wartości to `Version30` i `Version35`. Wartość domyślna to `Version30`.<br /><br /> Krótka forma:`/tcv`<br /><br /> `Version30`: Użyj `/tcv:Version30` Jeśli kod jest generowany dla klientów używających [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].<br /><br /> `Version35`: Użyj `/tcv:Version35` Jeśli kod jest generowany dla klientów używających [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Korzystając z `/tcv:Version35` z `/async` przełącznika zarówno oparty na zdarzeniach i generowane są oparte na wywołanie zwrotne/delegata metod asynchronicznych. Ponadto obsługa włączone LINQ zestawów danych i <xref:System.DateTimeOffset> jest włączona.|  
|/ opakowana|Określa, czy specjalne służy do stylem dokumentów z parametrami opakowana literał dokumentu. Użyj **/ opakowana** przełącznik z [narzędzie narzędzia metadanych modelu usług (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia, aby określić wielkość liter w normalnym.|  
  
> [!NOTE]
>  Jeśli powiązanie usługi jest jednym z powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md)) i <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwość jest ustawiona jako `None` lub `Sign`, Svcutil generuje plik konfiguracji przy użyciu [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu zamiast oczekiwanego elementu dostarczane przez system. Na przykład, jeśli usługa używa `<wsHttpBinding>` element z `ProtectionLevel` ustawioną `Sign`, został wygenerowany konfiguracji `<customBinding>` w sekcji powiązania zamiast `<wsHttpBinding>`. Aby uzyskać więcej informacji o poziomie ochrony, zobacz [poziom ochrony opis](../../../docs/framework/wcf/understanding-protection-level.md).  
  
### <a name="metadata-export"></a>Eksportowanie metadanych  
 Svcutil.exe można wyeksportować metadane dla usług, kontrakty i typów danych w zestawach skompilowany. Aby wyeksportować metadane dla usługi, należy użyć `/serviceName` opcję, aby określić usługę chcesz wyeksportować. Aby wyeksportować wszystkie typy kontraktu danych w zestawie, należy użyć `/dataContractOnly` opcji. Domyślnie metadane są eksportowane dla wszystkich umów usługi w zestawach wejściowych.  
  
 `svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`  
  
|Argument|Opis|  
|--------------|-----------------|  
|`assemblyPath`|Określa ścieżkę do zestawu, który zawiera typy kontraktu usługi, umowy lub danych do wyeksportowania. Symbole wieloznaczne standardowe wiersza polecenia mogą służyć do zapewnienia wiele plików jako dane wejściowe.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|/serviceName:\<serviceConfigName >|Określa nazwę konfiguracji usługi do wyeksportowania. Jeśli ta opcja jest używana, zestaw pliku wykonywalnego o skojarzony plik konfiguracji musi zostać przekazany jako dane wejściowe. Svcutil.exe przeszukuje wszystkie skojarzone pliki konfiguracji dla konfiguracji usługi. Jeśli pliki konfiguracji zawierają wszystkie typy rozszerzeń, zestawy, które zawierają te typy muszą być w pamięci GAC lub jawnie realizowane przy użyciu `/reference` opcji.|  
|/ reference:\<ścieżka pliku >|Dodaje określony zestaw do zestawu zestawów użyć w celu usunięcia odwołania do typu. Jeśli podczas eksportowania lub sprawdzania poprawności usługi, która używa rozszerzeń 3rd firm (zachowania, powiązania i elementy BindingElements) zarejestrowany w konfiguracji, użyj tej opcji, aby zlokalizować zestawów rozszerzenia, które nie znajdują się w pamięci GAC.<br /><br /> Krótka forma:`/r`|  
|/dataContractOnly|Działa na danych tylko dla typów kontraktu. Kontrakty usług nie są przetwarzane.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka forma:`/dconly`|  
|/excludeType:\<typu >|Określa pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu do wykluczenia z eksportu. Ta opcja może być używana podczas eksportowania metadanych dla usługi lub zbiór usług umów do wykluczyć typy są eksportowane. Nie można użyć tej opcji wraz z `/dconly` opcji.<br /><br /> Gdy masz jednym zestawie zawierający wiele usług, a każda używa osobnych klas o takiej samej nazwie XSD, należy określić nazwę usługi, zamiast nazwy klasy XSD dla tego przełącznika.<br /><br /> Typy kontraktu danych lub XSD są nieobsługiwane.<br /><br /> Krótka forma:`/et`|  
  
### <a name="service-validation"></a>Weryfikacja usług  
 Sprawdzanie poprawności może służyć do wykrywania błędów w implementacji usługi bez obsługującego usługę. Należy użyć `/serviceName` opcję, aby wskazać usługi chcesz zweryfikować.  
  
 `svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`  
  
|Argument|Opis|  
|--------------|-----------------|  
|`assemblyPath`|Określa ścieżkę do zestawu, który zawiera typów usług do sprawdzenia poprawności. Zestaw musi mieć skojarzony plik konfiguracji zapewnienie konfiguracji usługi. Standardowa symboli wieloznacznych wiersza polecenia mogą służyć do zapewnienia wiele zestawów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|/ validate|Weryfikuje implementacji usługi, określony przez `/serviceName` opcji. Jeśli ta opcja jest używana, zestaw pliku wykonywalnego o skojarzony plik konfiguracji musi zostać przekazany jako dane wejściowe.<br /><br /> Krótka forma:`/v`|  
|/serviceName:\<serviceConfigName >|Określa nazwę konfiguracji usługi do sprawdzenia poprawności. Svcutil.exe przeszukuje wszystkie pliki konfiguracji skojarzone z zestawów wejściowych wszystkie dla konfiguracji usługi. Jeśli pliki konfiguracji zawierają wszystkie typy rozszerzeń, zestawy, które zawiera następujące typy muszą być w pamięci GAC lub jawnie realizowane przy użyciu `/reference` opcji.|  
|/ reference:\<ścieżka pliku >|Dodaje określony zestaw do zestawu zestawów użyć w celu usunięcia odwołania do typu. Jeśli podczas eksportowania lub sprawdzania poprawności usługi, która używa rozszerzeń 3rd firm (zachowania, powiązania i elementy BindingElements) zarejestrowany w konfiguracji, użyj tej opcji, aby zlokalizować zestawów rozszerzenia, które nie znajdują się w pamięci GAC.<br /><br /> Krótka forma:`/r`|  
|/dataContractOnly|Działa na danych tylko dla typów kontraktu. Kontrakty usług nie są przetwarzane.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka forma:`/dconly`|  
|/excludeType:\<typu >|Określa pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu do wykluczenia z weryfikacji.<br /><br /> Krótka forma:`/et`|  
  
### <a name="metadata-download"></a>Pobieranie metadanych  
 Svcutil.exe może służyć do pobierania metadanych z uruchomionymi usługami i zapisywania metadanych do plików lokalnych. Aby pobrać metadane, należy określić `/t:metadata` opcji. W przeciwnym razie generowania kodu klienta. Schematy HTTP i HTTPS URL Svcutil.exe próbuje pobrać metadanych za pomocą usługi WS-Metadata Exchange i DISCO. Inne schematy adresów URL Svcutil.exe używa tylko WS-Metadata Exchange.  
  
 Narzędzia svcutil wystawia następujące żądania metadanych jednocześnie do pobierania metadanych.  
  
-   Podany adres żądanie MEX (WS-Transfer)  
  
-   Podany adres z /mex dołączany MEX żądania  
  
-   DISCO żądanie (przy użyciu DiscoveryClientProtocol z ASMX) podany adres.  
  
 Domyślnie korzysta z powiązań zdefiniowanych w Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasie, aby MEX żądań. Aby skonfigurować powiązanie użyte dla WS-Metadata Exchange, należy zdefiniować punkt końcowy klienta w konfiguracji, który korzysta z kontraktem IMetadataExchange. Może to być określone w pliku konfiguracyjnym programu Svcutil.exe lub w innym pliku konfiguracji, określić przy użyciu `/svcutilConfig` opcji.  
  
 `svcutil.exe /t:metadata  <url>* | <epr>`  
  
|Argument|Opis|  
|--------------|-----------------|  
|`url`|Adres URL punktu końcowego usługi, która udostępnia metadane lub dokument metadanych, hostowana w trybie online.|  
|`epr`|Ścieżka do pliku XML, który zawiera WS-Addressing EndpointReference punktu końcowego usługi, która obsługuje WS-Metadata Exchange.|  
  
### <a name="xmlserializer-type-generation"></a>Generowanie typu XmlSerializer  
 Usługi i aplikacje klienckie, które używają typów danych, które są do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilacja kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować wolne uruchamiania wydajności.  
  
> [!NOTE]
>  Kod serializacji wstępnie wygenerowane można tylko w aplikacjach klienckich, a nie w usługach.  
  
 Svcutil.exe może spowodować wygenerowanie niezbędne kodu serializacji C# skompilowane zestawy dla aplikacji, co poprawia wydajność uruchamiania tych aplikacji. Aby uzyskać więcej informacji, zobacz [porady: poprawy uruchamiania czasu programu WCF aplikacje klienckie przy użyciu elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
> [!NOTE]
>  Svcutil.exe tylko generuje kod dla typów używanych przez kontraktów usług znaleziono w zestawach wejściowych.  
  
 `svcutil.exe /t:xmlSerializer  <assemblyPath>*`  
  
|Argument|Opis|  
|--------------|-----------------|  
|`assemblyPath`|Określa ścieżkę do zestawu, który zawiera typy kontraktu usługi. Typy serializacji są generowane dla wszystkich typów serializacji Xml w każdej umowy.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|/ reference:\<ścieżka pliku >|Dodaje określony zestaw do zestawu zestawów użyć w celu usunięcia odwołania do typu.<br /><br /> Krótka forma:`/r`|  
|/excludeType:\<typu >|Określa pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu do wykluczenia z weryfikacji lub eksportu.<br /><br /> Krótka forma:`/et`|  
|/ out:\<pliku >|Określa nazwę pliku dla wygenerowanego kodu. Ta opcja jest ignorowana, jeśli wiele zestawów są przekazywane jako dane wejściowe do narzędzia.<br /><br /> Wartość domyślna: Pochodzi od nazwy zestawu.<br /><br /> Krótka forma:`/o`|  
|/ UseSerializerForFaults|Określa, że <!--zz <xref:System.Xml.XmlSerializer> --> `xref:System.Xml.XmlSerializer ` powinna być używana do odczytywania i zapisywania błędów, zamiast domyślnej <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="examples"></a>Przykłady  
 Polecenie generuje kod klienta z uruchomioną usługę lub dokumentów metadanych online.  
  
 `svcutil http://service/metadataEndpoint`  
  
 Polecenie generuje kod klienta z metadanymi lokalnymi dokumentów.  
  
 `svcutil *.wsdl *.xsd /language:C#`  
  
 Polecenie generuje typy kontraktu danych w języku Visual Basic z lokalnym schematu dokumentów.  
  
 `svcutil /dconly *.xsd /language:VB`  
  
 Polecenie pobiera dokumentów metadanych z uruchomionymi usługami.  
  
 `svcutil /t:metadata http://service/metadataEndpoint`  
  
 Polecenie generuje dokumentów metadanych dla kontraktów usługi i związanych z nimi typów w zestawie.  
  
 `svcutil myAssembly.dll`  
  
 Polecenie generuje dokumentów metadanych dla usługi, a wszystkie skojarzone kontraktów usług i typy danych w zestawie.  
  
 `svcutil myServiceHost.exe /serviceName:myServiceName`  
  
 Polecenie generuje dokumentów metadanych dla typów danych w zestawie.  
  
 `svcutil myServiceHost.exe /dconly`  
  
 Polecenie sprawdza hostingu usług.  
  
 `svcutil /validate /serviceName:myServiceName myServiceHost.exe`  
  
 Polecenie generuje typy serializacji dla <xref:System.Xml.Serialization.XmlSerializer> typy używane przez wszystkie kontrakty usług w zestawie.  
  
 `svcutil /t:xmlserializer myContractLibrary.exe`  
  
## <a name="maximum-nametable-character-count-quota"></a>Niepowtarzającymi maksymalny przydział liczby znaków  
 Generowanie metadanych dla usługi za pomocą narzędzia svcutil, mogą pojawić się następujący komunikat:  
  
 Błąd: Nie można uzyskać metadanych z http://localhost: 8000/somesservice/mex, który podczas odczytywania danych XML został przekroczony maksymalny przydział liczby znaków (16384). Tabela nazw jest strukturą danych używaną do przechowywania ciągów napotkanych podczas przetwarzania XML — długie dokumenty XML z niepowtarzającymi nazwy elementów, nazwami atrybutów i wartościami atrybutów mogą spowodować przekroczenie tego przydziału. Tę można zwiększyć, zmieniając właściwość MaxNameTableCharCount obiektu XmlDictionaryReaderQuotas użytego podczas tworzenia modułu odczytującego XML.  
  
 Ten błąd może być spowodowany przez usługę, która zwraca dużego pliku WSDL, w przypadku żądania metadanych. Problem polega na przekroczenie przydziału znak z narzędzia svcutil.exe. Ta wartość jest równa pomagać w zapobieganiu atakom DOS (dos). Określając następującego pliku konfiguracji dla narzędzia svcutil, można zwiększyć ten limit przydziału.  
  
 Następujący plik konfiguracji przedstawiono sposób ustawiania przydziałów czytnik dla narzędzia svcutil  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <customBinding>  
                <binding name="MyBinding">  
                    <textMessageEncoding>  
                        <readerQuotas maxDepth="2147483647" maxStringContentLength="2147483647"  
                            maxArrayLength="2147483647" maxBytesPerRead="2147483647" maxNameTableCharCount="2147483647" />  
                    </textMessageEncoding>  
                    <httpTransport maxReceivedMessageSize="2147483647" maxBufferSize="2147483647" />  
                </binding>  
            </customBinding>  
        </bindings>  
        <client>  
            <endpoint binding="customBinding" bindingConfiguration="MyBinding"  
                contract="IMetadataExchange"  
                name="http" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 Utwórz nowy plik o nazwie svcutil.exe.config i skopiuj do niego przykładowy kod XML. Następnie należy umieścić plik w tym samym katalogu co svcutil.exe. Przy następnym uruchomieniu svcutil.exe spowoduje pobranie nowych ustawień.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
 Odpowiednie listy kontroli dostępu (ACL) należy używać do ochrony folderu instalacji, Svcutil.config i plików jest wskazywana przez jego Svcutil.exe `/svcutilConfig`. Może to spowodować, że złośliwe rozszerzenia zarejestrowane i uruchom.  
  
 Ponadto aby zminimalizować ryzyko naruszenia zabezpieczeń, nie należy dodawać niezaufanych rozszerzenia jako część systemu, ani dostawców kodzie niezaufanym za pomocą Svcutil.exe.  
  
 Ponadto nie należy używać narzędzia w warstwie środkowej aplikacji, ponieważ może to spowodować odmowę usługi do bieżącego procesu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
