---
title: Przegląd architektury metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: f9c903dd520f1aa85fc0577264288ecbc8c62a7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046573"
---
# <a name="metadata-architecture-overview"></a>Przegląd architektury metadanych
Windows Communication Foundation (WCF) zapewnia rozbudowane infrastrukturę na potrzeby eksportowania, publikowania, pobieranie i Importowanie metadanych usługi. Usługi WCF umożliwia metadane opisują sposób interakcji z punktami końcowymi usługi, tak aby narzędzi, takich jak Svcutil.exe, może automatycznie generować kod klienta do uzyskania dostępu do usługi.  
  
 Większość typów, które tworzą infrastruktura metadanych WCF znajdują się w <xref:System.ServiceModel.Description> przestrzeni nazw.  
  
 Korzysta z usługi WCF <xref:System.ServiceModel.Description.ServiceEndpoint> klasę do opisania punktów końcowych w usłudze. Usługi WCF umożliwia generowanie metadanych dla punktów końcowych usługi lub importowanie metadanych usługi w celu wygenerowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień.  
  
 Usługi WCF reprezentuje metadane dla usługi jako wystąpienie <xref:System.ServiceModel.Description.MetadataSet> typ struktury jest ściśle powiązane format serializacji metadanych, które są zdefiniowane w WS-MetadataExchange. <xref:System.ServiceModel.Description.MetadataSet> Typu razem rzeczywistej usługi metadanych, takich jak dokumenty z sieci Web Services Description Language (WSDL), dokumentów schematu XML lub wyrażenia WS-Policy jako kolekcja <xref:System.ServiceModel.Description.MetadataSection> wystąpień. Każdy <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> wystąpienie zawiera dialekt określonych metadanych i identyfikator. A <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> może zawierać następujące elementy w jego <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> właściwości:  
  
- Surowych metadanych.  
  
- A <xref:System.ServiceModel.Description.MetadataReference> wystąpienia.  
  
- A <xref:System.ServiceModel.Description.MetadataLocation> wystąpienia.  
  
 A <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> wystąpień wskaż inny punkt końcowy metadanych programu exchange (MEX) i <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> wystąpień wskaż dokumentu metadanych za pomocą adresu URL HTTP. Obsługa programu WCF za pomocą dokumenty WSDL opisano punkty końcowe usługi, kontraktów usług, wiązania, wzorce wymiany komunikatów, wiadomości i komunikaty o błędach implementowane przez usługę. Typy danych używany przez usługę są opisane w dokumenty WSDL przy użyciu schematu XML. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). Za pomocą usług WCF do eksportowania i importowania rozszerzenia WSDL zachowanie usługi, zachowań kontraktu i elementy powiązań, które rozszerzają funkcjonalność usługi. Aby uzyskać więcej informacji, zobacz [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Eksportowanie metadanych usługi  
 W programie WCF *eksportowania metadanych* to proces opisujące punkty końcowe usługi i wyświetlaniu je do reprezentacji równoległych, standardowe, której klienci mogą używać, aby zrozumieć sposób korzystania z usługi. Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień, korzystać z implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementacji generuje metadanych, które są hermetyzowane w <xref:System.ServiceModel.Description.MetadataSet> wystąpienia.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Klasy zapewnia platformę do generowania wyrażeń zasad, które opisują możliwości i wymagania powiązanie punktu końcowego i jego skojarzone operacje, wiadomości i błędy. Wyrażenia te zasady są przechwytywane <xref:System.ServiceModel.Description.PolicyConversionContext> wystąpienia. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementacji następnie dołączyć te wyrażenia zasad do metadanych generuje.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Wywołania do każdej z nich <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> implementującej <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu w powiązaniu z <xref:System.ServiceModel.Description.ServiceEndpoint> podczas generowania <xref:System.ServiceModel.Description.PolicyConversionContext> dla obiektu <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> wdrożenia do użycia. Możesz wyeksportować nowej asercji zasad przez zaimplementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu na swoje niestandardowe implementacje <xref:System.ServiceModel.Channels.BindingElement> typu.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typu jest implementacją <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> abstrakcyjna klasa dołączone do programu WCF. <xref:System.ServiceModel.Description.WsdlExporter> Typu generuje WSDL metadanych za pomocą wyrażenia zasad dołączone.  
  
 Aby wyeksportować niestandardowych metadanych WSDL lub rozszerzenia WSDL dla zachowań punktu końcowego, zachowania kontraktu lub elementy powiązania punktu końcowego usługi, można zaimplementować <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu. <xref:System.ServiceModel.Description.WsdlExporter> Analizuje <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienie dla wiązania elementów, operacja zachowań, zachowania kontraktu i zachowań punktu końcowego, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejs podczas generowania dokumentu WSDL.  
  
## <a name="publishing-service-metadata"></a>Publikowanie metadanych usługi  
 Usługi WCF Publikowanie metadanych przez udostępnianie punkty końcowe metadanych. Publikowanie metadanych usługi udostępnia metadane usługi za pomocą standardowych protokołów, takich jak żądania MEX i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają adres, powiązanie i kontrakt. Punkty końcowe metadanych można dodać do hosta usługi w konfiguracji lub w kodzie.  
  
 Aby opublikować punkty końcowe metadanych dla usługi WCF, należy najpierw dodać wystąpienia <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowanie do usługi. Dodawanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpień z usługą rozszerza usługi z możliwością Publikowanie metadanych przez udostępnianie punkty końcowe metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowanie usługi należy następnie udostępnić punkty końcowe metadanych, które obsługują MEX protokołu lub metadanych punktów końcowych, które odpowiadają na żądania HTTP/GET.  
  
 Aby dodać punkty końcowe metadanych, które używają protokołu MEX, Dodaj punkty końcowe usługi do hosta usługi używanego przez kontraktu usługi o nazwie IMetadataExchange.WCF definiuje <xref:System.ServiceModel.Description.IMetadataExchange> interfejsu, który ma ta nazwa kontraktu usługi. Punkty końcowe usługi WS-MetadataExchange lub MEX punktów końcowych, można użyć jednej z czterech domyślne powiązania, udostępnianych przez statycznych metod fabryki na <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy, aby dopasować domyślne powiązania, używany przez narzędzia WCF, takie jak Svcutil.exe. Można również skonfigurować MEX punktów końcowych metadanych przy użyciu niestandardowego powiązania.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Używa <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Aby wyeksportować metadane dla wszystkich punktów końcowych usługi w usłudze. Aby uzyskać więcej informacji na temat eksportowania metadanych z usługi, zobacz [eksportowania i importowania metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Rozszerzają hosta usług, dodając <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienia jako rozszerzenie do hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Udostępnia implementację dla publikowania protokołów metadanych. Można również użyć <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> można pobrać metadanych usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> właściwości.  
  
> [!CAUTION]
> Jeśli dodasz punktu końcowego MEX w pliku konfiguracyjnym aplikacji, a następnie nastąpi próba dodania <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do hosta usługi w kodzie, otrzymasz następujący wyjątek:  
>
> System.InvalidOperationException: Nie można odnaleźć nazwy kontraktu "IMetadataExchange" na liście umów implementowane przez usługę Service1. Dodaj obiekt ServiceMetadataBehavior do pliku konfiguracji lub ServiceHost bezpośrednio po to, aby włączyć obsługę dla tego kontraktu.  
>
> Można obejść ten problem, dodając <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w pliku konfiguracji lub dodawanie zarówno punktu końcowego i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w kodzie.  
>
> Na przykład dodanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w pliku konfiguracji aplikacji, zobacz [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Na przykład dodanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w kodzie, zobacz [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.  

> [!CAUTION]
> Każda zawiera operację o takiej samej nazwie wyjątek jest generowany, gdy publikowanie metadanych dla usługi, który udostępnia dwa różne usług kontraktów. Na przykład jeśli masz usługę, która udostępnia kontraktu usługi o nazwie ICarService, który ma operacji Pobierz (samochód c) i tej samej usłudze udostępnia kontraktu usługi o nazwie IBookService, która ma operację Get (książka b), zgłaszany jest wyjątek lub komunikat o błędzie wyświetlany podczas generowania metadanych usługi. W celu obejścia tego problemu, wykonaj, jedną z następujących czynności:  
>
> - Zmień nazwę jednej z operacji.
> - Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na inną nazwę.  
> - Wartość jednej z operacji w przestrzeni nazw za pomocą różnych nazw <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
## <a name="retrieving-service-metadata"></a>Podczas pobierania metadanych usługi  
 Usługi WCF można pobrać metadanych usługi za pomocą standardowych protokołów, takich jak usługi WS-MetadataExchange i HTTP. Obu tych protokołów są obsługiwane przez <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Możesz pobrać metadanych usługi przy użyciu <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu, podając adres i powiązanie opcjonalne. Wiązanie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia może być jednym z domyślne powiązania z <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy statycznej, powiązanie dostarczone przez użytkownika lub powiązanie ładowane z konfiguracji punktu końcowego dla `IMetadataExchange` kontraktu. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Również może rozpoznać odwołania URL protokołu HTTP do korzystania z metadanych <xref:System.Net.HttpWebRequest> typu.  
  
 Domyślnie <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia jest powiązana z pojedynczej <xref:System.ServiceModel.Channels.ChannelFactoryBase> wystąpienia. Możesz zmienić lub Zastąp <xref:System.ServiceModel.Channels.ChannelFactoryBase> wystąpienia używanego przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> metodę wirtualną. Podobnie, można zmienić lub Zastąp <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> wystąpienia używanego przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> na wysyłanie żądań HTTP/GET przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> metodę wirtualną.  
  
 Można pobrać metadanych usługi przy użyciu żądania WS-MetadataExchange lub HTTP/GET, korzystając z narzędzia Svcutil.exe i przekazując **/target:metadata** przełącznika i adresu. Svcutil.exe pliki do pobrania metadanych pod określonym adresem i zapisuje pliki na dysku. Używa svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia wewnętrznie i obciążeń MEX konfiguracji punktu końcowego (z pliku konfiguracji aplikacji) którego nazwa odpowiada schemat adresu przekazanego Svcutil.exe, jeśli taki istnieje. W przeciwnym razie Svcutil.exe domyślnie korzysta z jednego z powiązań zdefiniowanych przez <xref:System.ServiceModel.Description.MetadataExchangeBindings> typu statycznego fabryki.  
  
## <a name="importing-service-metadata"></a>Importowanie metadanych usługi  
 W programie WCF Importowanie metadanych jest proces generowania abstrakcyjną reprezentację usługi lub jej części składowe z jego metadanych. Na przykład, można zaimportować WCF <xref:System.ServiceModel.Description.ServiceEndpoint> przypadkach <xref:System.ServiceModel.Channels.Binding> wystąpień lub <xref:System.ServiceModel.Description.ContractDescription> wystąpień na podstawie pliku WSDL dokumentów dla usługi. Aby zaimportować metadane usługi w programie WCF, należy korzystać z implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. Typy, które wynikają z <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasa implementuje pomocy technicznej w przypadku importowania formaty metadanych, które korzystają z protokołu WS-Policy zaimportować logiki w programie WCF.  
  
 A <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> implementacji zbiera wyrażeń zasad, dołączony do metadanych usługi w <xref:System.ServiceModel.Description.PolicyConversionContext> obiektu. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> Następnie przetwarza zasad w ramach importowania metadanych przez wywołanie metody implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu w <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> właściwości.  
  
 Można dodać obsługę nowej asercji zasad do importowania <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> przez dodanie własnych implementacji <xref:System.ServiceModel.Description.IPolicyImportExtension> współpracować w celu <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji na <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> wystąpienia. Alternatywnie można zarejestrować rozszerzenia importu zasad w pliku konfiguracyjnym aplikacji klienta.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu jest implementacją <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstrakcyjna klasa dołączone do programu WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu importuje metadane WSDL z dołączonym zasadami, które są powiązane w <xref:System.ServiceModel.Description.MetadataSet> obiektu.  
  
 Można dodać Obsługa importowania rozszerzenia WSDL przez zaimplementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejsu, a następnie dodając do implementacji <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> właściwość swoje <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> wystąpienia. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Można również załadować implementacje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejs zarejestrowany w pliku konfiguracyjnym aplikacji klienta.  
  
## <a name="dynamic-bindings"></a>Dynamiczne powiązania  
 Może dynamicznie aktualizować powiązania, którego używasz do utworzenia kanału do punktu końcowego usługi, w przypadku, gdy zmieni się powiązanie dla punktu końcowego, lub jeśli chcesz utworzyć kanał powiadomień do punktu końcowego, który używa tej samej umowy, ale ma inne powiązanie. Możesz użyć <xref:System.ServiceModel.Description.MetadataResolver> klasy statycznej, pobieranie i Importowanie metadanych w czasie wykonywania dla punktów końcowych usługi, które implementują określone kontraktu. Następnie można użyć zaimportowanych <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> obiektów, aby utworzyć fabrykę klienta lub kanał do żądanego punktu końcowego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description>
- [Formaty metadanych](../../../../docs/framework/wcf/feature-details/metadata-formats.md)
- [Eksportowanie i importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
- [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [Pobieranie metadanych](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
