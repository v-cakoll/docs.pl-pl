---
title: Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: f9ae53aeb988f23611adb4b00354f65918790d3b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200766"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)

Narzędzie metadanych elementu ServiceModel narzędzie służy do generowania kodu modelu usługi z dokumentów metadanych i dokumentów metadanych z kodu modelu usługi.

## <a name="svcutilexe"></a>SvcUtil.exe

Narzędzie narzędzie metadanych elementu ServiceModel znajduje się w lokalizacji instalacji zestawu Windows SDK specjalnie *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*.

### <a name="functionalities"></a>Funkcje

Poniższa tabela zawiera podsumowanie różnych funkcji udostępnianych przez to narzędzie i odpowiedni temat, który w tym artykule omówiono, jak jest używany:

|Zadanie|Temat|
|----------|-----------|
|Generuje kod z uruchomionych usług lub statycznych dokumentów metadanych.|[Generowanie klienta programu WCF na podstawie metadanych usługi](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|
|Eksportuje dokumentów metadanych ze skompilowanego kodu.|[Instrukcje: eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|Sprawdza poprawność skompilowanego kodu usługi.|[Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|Pobiera dokumentów metadanych z uruchomionymi usługami.|[Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|Generuje kod serializacji.|[Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> Narzędzia svcutil zastępuje istniejące pliki na dysku, jeśli dostarczone jako parametry nazwy są identyczne. Może to obejmować pliki kodu, konfiguracji lub pliki metadanych. Aby tego uniknąć podczas generowania kodu i konfiguracji prostej, użyj `/mergeConfig` przełącznika.
>
> Ponadto `/r` i `/ct` przełączników do odwoływania się do typów są do generowania kontraktów danych. Te przełączniki nie będą działać przy użyciu elementu XmlSerializer.

### <a name="timeout"></a>limit czasu

Narzędzie ma limit pięciu minut, podczas pobierania metadanych. Tego limitu czasu ma zastosowanie tylko do pobierania metadanych za pośrednictwem sieci. Nie ma zastosowania do jakiegokolwiek przetwarzania tych metadanych.

### <a name="multi-targetting"></a>Obsługa wielu odwołujących

Narzędzie nie obsługuje wielowersyjności kodu. Jeśli chcesz wygenerować artefaktu .NET 4 *svcutil.exe*, użyj *svcutil.exe* z zestawu SDK .NET 4. Aby wygenerować artefaktu .NET 3.5, należy użyć pliku wykonywalnego z zestawu SDK programu .NET 3.5.

### <a name="accessing-wsdl-documents"></a>Uzyskiwanie dostępu do dokumentów w formacie WSDL

Gdy używasz narzędzia Svcutil dostępu do dokumentu WSDL, który odwołuje się do usługi tokenu zabezpieczającego (STS), narzędzia Svcutil sprawia, że usługi WS-MetadataExchange wywołań do usługi STS. Jednak usługa mogą uwidocznić swoje dokumenty WSDL, za pomocą usługi WS-MetadataExchange lub HTTP GET. W związku z tym jeśli usługi STS jest dostępne tylko przy użyciu HTTP GET klienta napisanego w dokumencie WSDL [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] zakończy się niepowodzeniem. W przypadku klientów, napisany w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]Svcutil podejmują próbę użycia obu WS-MetadataExchange i HTTP GET w celu uzyskania WSDL usługi STS.

## <a name="using-svcutilexe"></a>Za pomocą SvcUtil.exe

### <a name="common-usages"></a>Typowego użycia

W poniższej tabeli przedstawiono niektóre najczęściej używanych opcji dla tego narzędzia:

|Opcja|Opis|
|------------|-----------------|
|/ katalog:\<katalogu >|Katalog, w którym będą tworzone pliki.<br /><br /> Domyślnie: Bieżący katalog.<br /><br /> Krótka: `/d`|
|/help|Wyświetla składnię polecenia i opcje narzędzia.<br /><br /> Krótka: `/?`|
|/ nologo|Pomiń komunikat o prawach autorskich i baneru.|
|/svcutilConfig:\<configFile>|Określa plik konfiguracji niestandardowej do użycia zamiast pliku App.config. To może służyć do zarejestrowania rozszerzenia system.serviceModel nie zmieniając pliku konfiguracji tego narzędzia.|
|/ target:\<typ danych wyjściowych >|Określa dane wyjściowe zostanie wygenerowany przez narzędzie.<br /><br /> Prawidłowe wartości to kod, metadanych lub elementu xmlSerializer.<br /><br /> Krótka: `/t`|

### <a name="code-generation"></a>Generowanie kodu

Svcutil.exe może wygenerować kod dla usługi kontrakty, klientów i typy danych z dokumentów metadanych. Te dokumenty metadanych mogą znajdować się na trwałego magazynu lub pobierana w trybie online. Pobieranie online następuje protokołu WS-Metadata Exchange lub protokołu NAJDYWANIA (Aby uzyskać szczegółowe informacje, zobacz sekcję Pobieranie metadanych).

Możesz użyć *SvcUtil.exe* narzędzie do generowania kontraktów usług i danych na podstawie wstępnie zdefiniowanych dokumentu WSDL. Użyj przełącznika /serviceContract i określ adres URL lub lokalizacji pliku, gdzie dokument WSDL, można pobrać lub znaleźć. Spowoduje to wygenerowanie kontraktów usług i danych, zdefiniowane w dokumencie WSDL, który następnie może służyć do implementacji usługi skargi. Aby uzyskać więcej informacji, zobacz [porady: Pobieranie metadanych i implementowanie zgodnej usługi](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).

Usługi za pomocą punktu końcowego obiekt BasicHttpContextbinding *Svcutil.exe* generuje BasicHttpBinding z `allowCookies` ustawioną wartość atrybutu `true` zamiast tego. Pliki cookie są używane w kontekście na serwerze. Jeśli chcesz zarządzać kontekstu na komputerze klienckim, gdy usługa używa plików cookie, można ręcznie zmodyfikować tę konfigurację na używanie kontekstu powiązania.

> [!CAUTION]
> Svcutil.exe generuje klienta na podstawie pliku WSDL lub zasad, otrzymanych z usługi. Główna nazwa użytkownika (UPN) jest generowana przez połączenie nazwy użytkownika, "\@" i w pełni kwalifikowaną nazwą domeny (FQDN). Jednak dla użytkowników, którzy zarejestrowali się w usłudze Active Directory, ten format jest nieprawidłowy i głównej nazwy użytkownika generowany przez narzędzie powoduje awarię w uwierzytelnianiu Kerberos z komunikatem o błędzie "Nie powiodła się próba logowania". Aby rozwiązać ten problem, należy ręcznie rozwiązać pliku klienta generowane przez to narzędzie.

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|Argument|Opis|
|--------------|-----------------|
|`epr`|Ścieżka do pliku XML, który zawiera WS-Addressing EndpointReference dla punktu końcowego usługi, który obsługuje usługi WS-Metadata Exchange. Aby uzyskać więcej informacji zobacz sekcję pobierania metadanych.|
|`metadataDocumentPath`|Ścieżka do dokumentu metadanych (*wsdl* lub *xsd*) zawierający umowy, aby importować do kodu (.wsdl, XSD, .wspolicy lub .wsmex).<br /><br /> Narzędzia svcutil następuje Importy i obejmuje po określeniu zdalny adres URL metadanych. Jednak jeśli użytkownik chce przetwarzać pliki metadanych w lokalnym systemie plików, należy określić wszystkie pliki w tym argumencie. W ten sposób można użyć narzędzia Svcutil w środowisku kompilacji gdzie nie może mieć zależności sieciowych. Można używać symboli wieloznacznych (*.xsd, \*.wsdl) dla tego argumentu.|
|`url`|Adres URL punktu końcowego usługi, który udostępnia metadane lub dokumentu z metadanymi hostowanego w trybie online. Aby uzyskać więcej informacji na temat sposobu te dokumenty są pobierane zobacz sekcję pobierania metadanych.|

|Opcja|Opis|
|------------|-----------------|
|/async|Generuje podpisy obu metod synchroniczne i asynchroniczne.<br /><br /> Wartość domyślna: generowanie tylko podpisy metod synchronicznych.<br /><br /> Krótka: `/a`|
|/collectionType:\<typ >|Określa typ kolekcji listy dla klienta programu WCF.<br/><br /> Wartość domyślna: typ kolekcji jest System.Array. <br /><br /> Krótka: `/ct`|
|/ config:\<configFile >|Określa nazwę pliku dla pliku wygenerowaną konfigurację.<br /><br /> Domyślne: output.config|
|/dataContractOnly|Generuje kod dla tylko typy kontraktu danych. Nie są generowane typy kontraktu usługi.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka: `/dconly`|
|/enableDataBinding|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu na wszystkich typach kontraktu danych umożliwiające powiązanie danych.<br /><br /> Krótka: `/edb`|
|/excludeType:\<typ >|Określa nazwę typu w pełni kwalifikowaną lub kwalifikowaną dla zestawu, które mają być wykluczone z typów kontraktu odwołania.<br /><br /> Korzystając z tego przełącznika, wraz z `/r` z oddzielnych bibliotek DLL, mowa Pełna nazwa klasy XSD.<br /><br /> Krótka: `/et`|
|/importXmlTypes|Konfiguruje serializatora kontraktu danych do importowania typów kontraktu danych jako typów IXmlSerializable.|
|/ wewnętrzny|Generuje klasy, które są oznaczone jako wewnętrzne. Wartość domyślna: Generuj klasy publiczne tylko.<br /><br /> Krótka: `/i`|
|/Language:\<języka >|Określa język programowania na potrzeby generowania kodu. Należy podać nazwę języka zarejestrowanych w pliku Machine.config lub w pełni kwalifikowaną nazwę klasy, która dziedziczy <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Wartości: c#, cs, csharp, vb, języka Visual Basic, c ++, cpp<br /><br /> Domyślne: csharp<br /><br /> Krótka: `/l`|
|/mergeConfig|Scala wygenerowaną konfigurację istniejącego pliku, zamiast nadpisywać istniejący plik.|
|/messageContract|Generuje typy kontraktu komunikatu.<br /><br /> Krótka: `/mc`|
|/ NAMESPACE:\<string, string >|Określa mapowanie targetNamespace schematu WSDL lub XML do przestrzeni nazw CLR. Za pomocą "\*" dla elementu targetNamespace spowoduje mapowanie wszystkich elementów targetNamespace bez jawnego mapowania na przestrzeń nazw CLR.<br /><br /> Aby upewnić się, że nazwa kontraktu komunikatu nie kolidujący operacji o nazwie, należy albo kwalifikujesz się do typu odwołanie z `::`, lub upewnij się, że nazwy są unikatowe.<br /><br /> Wartość domyślna: Pochodzi z docelowej przestrzeni nazw dokumentu schematu dla kontraktów danych. Domyślny obszar nazw jest używana dla wszystkich innych wygenerowanych typów.<br /><br /> Krótka: `/n` **Uwaga:** podczas generowania typów za pomocą elementu XmlSerializer, mapowanie jednej przestrzeni nazw jest obsługiwana. Wszystkich typów wygenerowanego będzie domyślny obszar nazw lub przestrzeni nazw określonej przez ' *'.|
|/ noconfig|Nie generują pliki konfiguracji.|
|/noStdLib|Nie odwołuj się do standardowych bibliotek.<br /><br /> Wartość domyślna: Mscorlib.dll i System.servicemodel.dll do których istnieją odwołania.|
|/ out:\<pliku >|Określa nazwę pliku dla wygenerowanego kodu.<br /><br /> Wartość domyślna: Pochodzi z nazwy definicji WSDL, nazwy usługi WSDL lub docelowa przestrzeń nazw jednego ze schematów.<br /><br /> Krótka: `/o`|
|/ reference:\<ścieżka pliku >|Typy odwołań w określonym zestawie. Podczas generowania klientów Użyj tej opcji, aby określić zestawy, które mogą zawierać typy reprezentujące importowane metadane.<br /><br /> Nie można określić kontrakty komunikatów i <xref:System.Xml.Serialization.XmlSerializer> typów za pomocą tego przełącznika.<br /><br /> Jeśli <xref:System.DateTimeOffset> odwołania, ten typ jest używany zamiast generowania nowego typu. Jeśli aplikacja jest napisane przy użyciu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], odwołania SvcUtil.exe <xref:System.DateTimeOffset> automatycznie.<br /><br /> Krótka: `/r`|
|/ możliwy do serializacji|Generuje klasy oznaczona przez atrybut możliwy do serializacji.<br /><br /> Krótka: `/s`|
|/serviceContract|Generuj kod dla tylko kontraktów usług. Klasa klienta i konfiguracji nie zostanie wygenerowany<br /><br /> Krótka: `/sc`|
|/serializer:Auto|Automatycznie wybierz serializator. To próbuje użyć serializatora kontraktu danych i używa serializatora XmlSerializer, jeśli się nie powiedzie.<br /><br /> Krótka: `/ser`|
|/serializer:DataContractSerializer|Generuje typy danych używające serializatora kontraktu danych do serializacji i deserializacji.<br /><br /> Krótka: `/ser:DataContractSerializer`|
|/serializer:XmlSerializer|Generuje typy danych, które używają <xref:System.Xml.Serialization.XmlSerializer> do serializacji i deserializacji.<br /><br /> Krótka: `/ser:XmlSerializer`|
|/targetClientVersion|Określ wersję [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji jest adresowany. Prawidłowe wartości to `Version30` i `Version35`. Wartość domyślna to `Version30`.<br /><br /> Krótka: `/tcv`<br /><br /> `Version30`: Służy `/tcv:Version30` klientów korzystających z generowania kodu [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].<br /><br /> `Version35`: Służy `/tcv:Version35` klientów korzystających z generowania kodu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Korzystając z `/tcv:Version35` z `/async` Przełącz zarówno oparte na zdarzeniach i generowane są oparte na wywołanie zwrotne/delegatach metod asynchronicznych. Ponadto obsługa komputerów z obsługą zapytań LINQ z zestawami danych i <xref:System.DateTimeOffset> jest włączona.|
|/ opakowana|Określa, czy specjalne jest używane różne dokumentów za pomocą parametrów opakowana literał dokumentu. Użyj **/ opakowane** przełącznik z [Service Model metadanych narzędzie (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia do określania normalnego wielkości liter.|

> [!NOTE]
> Gdy powiązanie usługi jest jednym z powiązań dostarczanych przez system (zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md)) i <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwość jest ustawiona jako `None` lub `Sign`, narzędzia Svcutil generuje plik konfiguracji przy użyciu [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu zamiast oczekiwanego elementu dostarczane przez system. Na przykład, jeśli usługa używa `<wsHttpBinding>` element z `ProtectionLevel` równa `Sign`, ma wygenerowaną konfigurację `<customBinding>` w sekcji wiązania zamiast `<wsHttpBinding>`. Aby uzyskać więcej informacji na temat poziomu ochrony, zobacz [zrozumieć poziom ochrony](../../../docs/framework/wcf/understanding-protection-level.md).

### <a name="metadata-export"></a>Eksportowanie metadanych

Svcutil.exe można wyeksportować metadane dotyczące usług, kontrakty i typów danych w skompilowanych zestawach. Aby wyeksportować metadane dla usługi, należy użyć `/serviceName` opcję, aby określić usługi, które chcesz wyeksportować. Aby wyeksportować wszystkie typy kontraktu danych w zestawie, należy użyć `/dataContractOnly` opcji. Domyślnie eksportowane są metadane dla wszystkich zamówień w zestawach danych wejściowych.

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|Argument|Opis|
|--------------|-----------------|
|`assemblyPath`|Określa ścieżkę do zestawu, który zawiera typy kontraktu, usług, umowy lub danych do wyeksportowania. Symbole wieloznaczne standardowego wiersza polecenia można przekazać wiele plików jako dane wejściowe.|

|Opcja|Opis|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|Określa nazwę konfiguracji usługi do wyeksportowania. Jeśli ta opcja jest używana, przy użyciu pliku konfiguracji skojarzonego zestawu pliku wykonywalnego musi zostać przekazany jako dane wejściowe. Svcutil.exe wyszukuje wszystkie skojarzone pliki konfiguracji do konfiguracji usługi. Jeśli pliki konfiguracji zawierają wszystkie typy rozszerzeń, musi być w pamięci GAC zestawy, które zawierają te typy, lub podane jawnie za pomocą `/reference` opcji.|
|/ reference:\<ścieżka pliku >|Dodaje określony zestaw zbiór zestawów, używany do rozpoznawania odwołań do typu. Jeśli eksportujesz lub Sprawdzanie poprawności to usługa, która używa rozszerzeń innych firm 3 (zachowań, powiązania i elementy BindingElements) zarejestrowany w konfiguracji, użyj tej opcji do lokalizowania zestawów rozszerzenie, które nie znajdują się w pamięci podręcznej GAC.<br /><br /> Krótka: `/r`|
|/dataContractOnly|Operuje na danych tylko dla typów kontraktu. Kontrakty usług nie są przetwarzane.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka: `/dconly`|
|/excludeType:\<typ >|Określa w pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu, które mają być wykluczone z eksportu. Tej opcji można użyć podczas eksportowania metadanych dla usługi lub zbiór usług umów do wykluczenia typów są eksportowane. Tej opcji nie można używać razem z `/dconly` opcji.<br /><br /> Jeśli masz pojedynczy zestaw zawierający wiele usług, a każda używa osobnych klas o takiej samej nazwie XSD, należy określić nazwę usługi, zamiast nazwy klasy XSD dla tego przełącznika.<br /><br /> Typy kontraktu danych lub XSD są nieobsługiwane.<br /><br /> Krótka: `/et`|

### <a name="service-validation"></a>Sprawdzanie poprawności usługi

Sprawdzanie poprawności może służyć do wykrywania błędów w implementacji usługi bez obsługującego usługę. Należy użyć `/serviceName` opcję, aby określić usługi, którą chcesz zweryfikować.

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|Argument|Opis|
|--------------|-----------------|
|`assemblyPath`|Określa ścieżkę do zestawu, który zawiera typy usług, które ma zostać zweryfikowana. Zestaw musi mieć skojarzony plik konfiguracji do zapewnienia konfiguracji usługi. Standardowa symboli wieloznacznych wiersza polecenia mogą służyć do zapewnienia wielu zestawów.|

|Opcja|Opis|
|------------|-----------------|
|/ validate|Sprawdza poprawność implementacji usługi, określony przez `/serviceName` opcji. Jeśli ta opcja jest używana, przy użyciu pliku konfiguracji skojarzonego zestawu pliku wykonywalnego musi zostać przekazany jako dane wejściowe.<br /><br /> Krótka: `/v`|
|/serviceName:\<serviceConfigName>|Określa nazwę konfiguracji usługi ma zostać zweryfikowana. Svcutil.exe wyszukuje wszystkie pliki konfiguracji skojarzonych zestawów wszystkich danych wejściowych dla konfiguracji usługi. Jeśli pliki konfiguracji zawierają wszystkie typy rozszerzeń, musi być w pamięci GAC zestawy, które zawiera następujące typy, lub podane jawnie za pomocą `/reference` opcji.|
|/ reference:\<ścieżka pliku >|Dodaje określony zestaw zbiór zestawów, używany do rozpoznawania odwołań do typu. Jeśli eksportujesz lub Sprawdzanie poprawności to usługa, która używa rozszerzeń innych firm 3 (zachowań, powiązania i elementy BindingElements) zarejestrowany w konfiguracji, użyj tej opcji do lokalizowania zestawów rozszerzenie, które nie znajdują się w pamięci podręcznej GAC.<br /><br /> Krótka: `/r`|
|/dataContractOnly|Operuje na danych tylko dla typów kontraktu. Kontrakty usług nie są przetwarzane.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka: `/dconly`|
|/excludeType:\<typ >|Określa w pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu, które mają być wykluczone z weryfikacji.<br /><br /> Krótka: `/et`|

### <a name="metadata-download"></a>Pobieranie metadanych

Svcutil.exe może służyć do pobierania metadanych z uruchomionymi usługami, a następnie Zapisz metadane do plików lokalnych. Aby pobrać metadane, należy określić `/t:metadata` opcji. W przeciwnym razie kod klienta jest generowany. Schematy HTTP i HTTPS URL Svcutil.exe próbuje pobrać metadanych przy użyciu usługi WS-Metadata Exchange i NAJDYWANIA. Inne schematy adresów URL Svcutil.exe używa tylko protokołu WS-Metadata Exchange.

Narzędzia svcutil generuje następujące żądania metadanych równocześnie do pobierania metadanych.

- Podany adres żądanie MEX (WS-Transfer)

- Podany adres z /mex dołączany MEX żądanie

- DISCO żądanie (przy użyciu DiscoveryClientProtocol z ASMX) podany adres.

Domyślnie korzysta z powiązań zdefiniowanych w Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy, aby wprowadzić MEX żądań. Aby skonfigurować powiązania, używany dla protokołu WS-Metadata Exchange, należy zdefiniować punkt końcowy klienta w konfiguracji, który korzysta z kontraktem IMetadataExchange. Może to być określone w pliku konfiguracyjnym programu Svcutil.exe lub w innym pliku konfiguracji określony za pomocą `/svcutilConfig` opcji.

`svcutil.exe /t:metadata  <url>* | <epr>`

|Argument|Opis|
|--------------|-----------------|
|`url`|Adres URL punktu końcowego usługi, który udostępnia metadane lub dokumentu z metadanymi hostowanego w trybie online.|
|`epr`|Ścieżka do pliku XML, który zawiera WS-Addressing EndpointReference dla punktu końcowego usługi, który obsługuje usługi WS-Metadata Exchange.|

### <a name="xmlserializer-type-generation"></a>Generowania typów elementu XmlSerializer

Usługi i aplikacje klienckie, które używają typów danych, które są możliwe do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilowanie kodu serializacji dla tych typów danych w czasie wykonywania, co może skutkować wydajności uruchamiania powolne.

> [!NOTE]
> Serializacja wstępnie wygenerowanego kodu należy używać tylko w aplikacjach klienckich, a nie w usługach.

Svcutil.exe może generować niezbędny kod serializacji C# z skompilowanych zestawów aplikacji, w związku z tym zwiększanie wydajności uruchamiania dla tych aplikacji. Aby uzyskać więcej informacji, zobacz [instrukcje: skracanie uruchamiania czasu z klienta aplikacji WCF za pomocą elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

> [!NOTE]
> Svcutil.exe tylko generuje kod dla typów używanych przez kontraktów usług znajdujących się w zestawach danych wejściowych.

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|Argument|Opis|
|--------------|-----------------|
|`assemblyPath`|Określa ścieżkę do zestawu, który zawiera typy kontraktu usługi. Serializacja typów są generowane dla wszystkich typów możliwych do serializacji Xml w każdej umowy.|

|Opcja|Opis|
|------------|-----------------|
|/ reference:\<ścieżka pliku >|Dodaje określony zestaw zbiór zestawów, używany do rozpoznawania odwołań do typu.<br /><br /> Krótka: `/r`|
|/excludeType:\<typ >|Określa w pełni kwalifikowaną lub kwalifikowaną dla zestawu nazwę typu do wykluczenia z Eksport lub sprawdzania poprawności.<br /><br /> Krótka: `/et`|
|/ out:\<pliku >|Określa nazwę pliku dla wygenerowanego kodu. Ta opcja jest ignorowana, gdy wiele zestawów są przekazywane jako dane wejściowe do narzędzia.<br /><br /> Wartość domyślna: Pochodzi z nazwy zestawu.<br /><br /> Krótka: `/o`|
|/ UseSerializerForFaults|Określa, że <xref:System.Xml.Serialization.XmlSerializer> powinny być używane do odczytywania i zapisywania błędów zamiast domyślnego <xref:System.Runtime.Serialization.DataContractSerializer>.|

## <a name="examples"></a>Przykłady

Następujące polecenie generuje kod klienta z uruchomionej usługi lub dokumentów metadanych online.

`svcutil http://service/metadataEndpoint`

Następujące polecenie generuje kod klienta z lokalnych dokumentów metadanych.

`svcutil *.wsdl *.xsd /language:C#`

Następujące polecenie generuje typy kontraktu danych w języku Visual Basic z dokumentów schematu lokalnego.

`svcutil /dconly *.xsd /language:VB`

Następujące polecenie pobiera dokumentów metadanych z uruchomionymi usługami.

`svcutil /t:metadata http://service/metadataEndpoint`

Następujące polecenie generuje dokumentów metadanych dla kontraktów usług i skojarzonych typów w zestawie.

`svcutil myAssembly.dll`

Następujące polecenie generuje dokumentów metadanych dla usługi, a wszystkie skojarzone kontraktów usług i typy danych w zestawie.

`svcutil myServiceHost.exe /serviceName:myServiceName`

Następujące polecenie generuje dokumentów metadanych dla typów danych w zestawie.

`svcutil myServiceHost.exe /dconly`

Poniższe polecenie sprawdza, hostingu usług.

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

Następujące polecenie generuje typy serializacji dla <xref:System.Xml.Serialization.XmlSerializer> typy używane przez wszystkie kontraktów usług w zestawie.

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>Maksymalny przydział liczby znaków przydziału

Generowanie metadanych dla usługi za pomocą narzędzia svcutil, może zostać wyświetlony następujący komunikat:

Błąd: Nie można uzyskać metadanych z http://localhost:8000/somesservice/mex podczas odczytywania danych XML został przekroczony maksymalny przydział liczby znaków (16384). Tabela nazw jest strukturą danych używaną do przechowywania ciągów napotkanych podczas przetwarzania XML — długie dokumenty XML z innych niepowtarzającymi się nazwami, nazwami atrybutów i wartości atrybutów może spowodować przekroczenie tego przydziału. Tę można zwiększyć, zmieniając właściwość MaxNameTableCharCount obiektu XmlDictionaryReaderQuotas użytego podczas tworzenia modułu odczytującego XML.

Ten błąd może być spowodowany przez usługę, która zwraca dużego pliku WSDL, gdy żądanie metadanych. Problem polega na tym, czy zostanie przekroczony przydział znak narzędzia svcutil.exe. Ta wartość jest równa pomaga zapobiegać atakom typu odmowa usługi (dos). Możesz zwiększyć ten limit przydziału, określając następującego pliku konfiguracji dla narzędzia svcutil.

Następujący plik konfiguracji pokazuje, jak ustawić przydziały czytnika svcutil

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

Utwórz nowy plik o nazwie svcutil.exe.config i skopiuj przykładowy kod XML do niego. Następnie umieść plik w tym samym katalogu co svcutil.exe. Przy następnym uruchomieniu svcutil.exe go wybierze nowych ustawień.

## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń

Należy używać odpowiednie listy kontroli dostępu (ACL) do ochrony folderu instalacji, Svcutil.config i pliki wskazywany przez firmy Svcutil.exe `/svcutilConfig`. Może to spowodować, że złośliwe rozszerzenia zarejestrowane i uruchom.

Ponadto aby zminimalizować ryzyko naruszenia zabezpieczeń, nie należy dodawać niezaufane rozszerzenia części systemu, lub dostawców niezaufanego kodu za pomocą Svcutil.exe.

Ponadto nie należy używać narzędzia w środkowej warstwie aplikacji, ponieważ może to spowodować odmowę usługi dla bieżącego procesu.

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
