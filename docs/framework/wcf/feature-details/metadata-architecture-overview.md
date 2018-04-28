---
title: Przegląd architektury metadanych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bce838d9584480028c7b02d1ba19547fe208bf2c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="metadata-architecture-overview"></a>Przegląd architektury metadanych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zapewnia infrastrukturę sformatowanego eksportowania, publikowania, pobieranie i Importowanie metadanych usługi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi używają metadanych opisujących sposób interakcji z punktów końcowych usługi, dzięki czemu narzędzi, takich jak Svcutil.exe, może automatycznie generować kod klienta do uzyskiwania dostępu do usługi.  
  
 Większość typów, które tworzą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury metadanych znajdują się w <xref:System.ServiceModel.Description> przestrzeni nazw.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa <xref:System.ServiceModel.Description.ServiceEndpoint> klasy do opisywania punktów końcowych w usłudze. Można użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generowanie metadanych dla punktów końcowych usługi lub importowanie metadanych usługi do generowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reprezentuje metadanych dla usługi jako wystąpienie <xref:System.ServiceModel.Description.MetadataSet> typ struktury jest silnie powiązany zdefiniowane w WS-MetadataExchange format serializacji metadanych. <xref:System.ServiceModel.Description.MetadataSet> Typu zawiera rzeczywiste usługi metadanych, takich jak dokumenty Web Services Description Language (WSDL), dokumentach schematów XML lub wyrażenia WS-Policy jako kolekcja <xref:System.ServiceModel.Description.MetadataSection> wystąpień. Każdy <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> wystąpienie zawiera dialekt określonych metadanych i identyfikator. A <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> może zawierać następujące elementy w jego <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> właściwości:  
  
-   Nieprzetworzona metadanych.  
  
-   A <xref:System.ServiceModel.Description.MetadataReference> wystąpienia.  
  
-   A <xref:System.ServiceModel.Description.MetadataLocation> wystąpienia.  
  
 A <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> wystąpień wskaż inny punkt końcowy programu exchange (MEX) metadanych i <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> wystąpień wskaż dokumentu metadanych za pomocą adresu URL HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Umożliwia używanie dokumentów WSDL do opisywania punktów końcowych usługi, kontraktów usług, powiązań, komunikat wymiany wzorców, wiadomości i komunikatów "fault" zaimplementowana przez usługę. Typy danych używane przez usługę są opisane w dokumentacji WSDL przy użyciu schematu XML. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). Można użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do eksportowania i importowania rozszerzenia WSDL dla zachowania usługi, należy Zwiń zachowania i elementy wiązania, które zapewniają rozszerzenie funkcjonalności usługi. Aby uzyskać więcej informacji, zobacz [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Eksportowanie metadanych usługi  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], *eksportowania metadanych* jest proces opisujące punktów końcowych usługi i projekcji ich reprezentację równoległe, standardowe, której klienci mogą używać, aby zrozumieć sposób korzystania z usługi. Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień, korzystać z implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementacji generuje metadanych, które są umieszczane w <xref:System.ServiceModel.Description.MetadataSet> wystąpienia.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Klasa dostarcza strukturę dla generowania wyrażenia zasad, które opisano wymagania powiązanie punktu końcowego i jego skojarzone operacje, wiadomości i błędów. Wyrażenia te zasady są przechwytywane <xref:System.ServiceModel.Description.PolicyConversionContext> wystąpienia. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementacji następnie dołączyć do metadanych generuje wyrażenia te zasady.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Wywołania do każdego <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> implementującej <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu w powiązaniu z <xref:System.ServiceModel.Description.ServiceEndpoint> podczas generowania <xref:System.ServiceModel.Description.PolicyConversionContext> obiekt do <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> wdrożenia do użycia. Nowe potwierdzeń zasad można wyeksportować zaimplementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejs użytkownika niestandardowego implementacje <xref:System.ServiceModel.Channels.BindingElement> typu.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typu to implementacja <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> dołączone do klasy abstrakcyjnej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlExporter> Typu generuje WSDL metadanych za pomocą wyrażeń dołączone zasad.  
  
 Aby wyeksportować niestandardowych metadanych WSDL lub rozszerzenia WSDL dla zachowania punktu końcowego, zachowania kontraktu lub elementy powiązania punktu końcowego usługi, można zaimplementować <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu. <xref:System.ServiceModel.Description.WsdlExporter> Analizuje <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia dla powiązania elementów, zachowania operacja kontraktu zachowania i zachowania punktu końcowego, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu podczas generowania pliku WSDL.  
  
## <a name="publishing-service-metadata"></a>Publikowanie metadanych usługi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi Publikowanie metadanych przez udostępnianie punkty końcowe metadanych. Publikowanie metadanych usługi udostępnia metadane usługi za pomocą standardowych protokołów, takich jak żądania MEX i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają address, binding i kontrakt. Punkty końcowe metadanych można dodać do usługi hosta w konfiguracji lub w kodzie.  
  
 Aby opublikować punkty końcowe metadanych dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, należy najpierw dodać wystąpienia <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowania do usługi. Dodawanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpienia z usługą rozszerza usługi umożliwia publikowanie metadanych przez udostępnianie punkty końcowe metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowanie usługi można następnie udostępnić punkty końcowe metadanych, które obsługują MEX protokołu lub metadane punkty końcowe, które odpowiadają na żądania HTTP/GET.  
  
 Aby dodać punkty końcowe metadanych, które używają protokołu MEX, należy dodać punkty końcowe usługi do używanego kontraktu usługi o nazwie IMetadataExchange hosta usługi.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definiuje <xref:System.ServiceModel.Description.IMetadataExchange> interfejs o tej nazwie kontraktu usługi. Punkty końcowe usługi WS-MetadataExchange lub MEX punktów końcowych, można użyć jednej z powiązań cztery domyślne udostępnianych przez metody statycznej fabryki na <xref:System.ServiceModel.Description.MetadataExchangeBindings> powiązania domyślne używane przez klasę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] narzędzi, takich jak Svcutil.exe. Można także skonfigurować punkty końcowe metadanych MEX przy użyciu niestandardowego powiązania.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Używa <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Aby wyeksportować metadane dla wszystkich punktów końcowych usługi w usłudze. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Eksportowanie metadanych z usługą, zobacz [eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Wspomaga host usług przez dodanie <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienia jako rozszerzenie hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Udostępnia implementację dla publikowania protokołów metadanych. Można również użyć <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> można pobrać metadanych usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> właściwości.  
  
> [!CAUTION]
>  Jeśli dodawanie punktu końcowego MEX w pliku konfiguracyjnym aplikacji, a następnie spróbuj dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Twojego host usługi w kodzie otrzymasz następujący wyjątek:  
>   
>  System.InvalidOperationException: Nie można odnaleźć nazwy kontraktu "IMetadataExchange" na liście kontraktów zaimplementowanych przez usługi Service1. Dodaj obiekt ServiceMetadataBehavior do pliku konfiguracji lub ServiceHost bezpośrednio, aby włączyć obsługę tego kontraktu.  
>   
>  Można obejść ten problem, można dodawać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w pliku konfiguracji lub dodawanie zarówno punktu końcowego i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w kodzie.  
>   
>  Na przykład dodawania <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w pliku konfiguracyjnym aplikacji, zobacz [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Na przykład dodawania <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w kodzie, zobacz [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.  
  
> [!CAUTION]
>  Każda zawierać operacji o tej samej nazwie wyjątek jest generowany, gdy publikowanie metadanych dla usługi, która udostępnia dwa różne usług umów. Na przykład jeśli korzystasz z usługi, który ujawnia kontraktu usługi o nazwie ICarService zawierający operacji Get (samochód c) i tej samej usługi przedstawia kontraktu usługi o nazwie IBookService zawierający operacji Get (książka b), jest zgłaszany wyjątek lub komunikat o błędzie wyświetlany podczas generowania metadanych usługi. W celu obejścia tego problemu, w wykonaj jedną z następujących czynności:  
>   
>  -   Zmień nazwę jednej z operacji.  
> -   Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> pod inną nazwą.  
> -   Wartość jednej z operacji w przestrzeni nazw przy użyciu różnych nazw <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
## <a name="retrieving-service-metadata"></a>Pobieranie metadanych usługi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można pobrać metadanych usługi za pomocą standardowych protokołów, takich jak usługi WS-MetadataExchange i HTTP. Oba te protokoły są obsługiwane przez <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Możesz pobrać metadanych usługi przy użyciu <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu, podając adres i powiązanie opcjonalne. Powiązanie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienie może być jednym z powiązań domyślne z <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy statycznej, powiązanie dostarczone przez użytkownika lub powiązanie ładowane z konfiguracji punktu końcowego dla `IMetadataExchange` kontraktu. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Również może rozpoznać adres HTTP URL odwołania do metadanych za pomocą <xref:System.Net.HttpWebRequest> typu.  
  
 Domyślnie <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia jest powiązany z pojedynczym <xref:System.ServiceModel.Channels.ChannelFactoryBase> wystąpienia. Możesz zmienić lub Zastąp <xref:System.ServiceModel.Channels.ChannelFactoryBase> wystąpienie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> metoda wirtualna. Analogicznie, można zmienić lub Zastąp <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> wystąpienie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> na wysyłanie żądań HTTP/GET przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> metoda wirtualna.  
  
 Można pobrać metadanych usługi przy użyciu żądania WS-MetadataExchange lub HTTP/GET, korzystając z narzędzia Svcutil.exe i przekazywanie **/target:metadata** przełącznika i adresu. Svcutil.exe pobiera metadane pod określonym adresem i zapisuje pliki na dysku. Używa svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienie wewnętrznie i obciążenia w konfiguracji punktu końcowego MEX (z pliku konfiguracji aplikacji) którego nazwa odpowiada schemat adresu przekazany do Svcutil.exe, jeśli istnieje. W przeciwnym razie Svcutil.exe domyślnie korzysta z jednego z powiązań zdefiniowanych przez <xref:System.ServiceModel.Description.MetadataExchangeBindings> Typ fabryki statycznych.  
  
## <a name="importing-service-metadata"></a>Importowanie metadanych usługi  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], importu metadanych jest proces generowania abstrakcyjną reprezentacją usługi lub jego składniki z jego metadanych. Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień, <xref:System.ServiceModel.Channels.Binding> wystąpień lub <xref:System.ServiceModel.Description.ContractDescription> wystąpień z WSDL dokumentu usługi. Aby zaimportować metadane usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], korzystać z implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. Typy, które pochodzą z <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasa implementuje pomocy technicznej dla importowania formaty metadanych, które korzystają z protokołu WS-Policy zaimportować logikę w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 A <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> implementacji zbiera wyrażenia zasad, dołączony do metadanych usługi w <xref:System.ServiceModel.Description.PolicyConversionContext> obiektu. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> Następnie przetwarza zasady jako część Importowanie metadanych przez wywołanie metody implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu w <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> właściwości.  
  
 Można dodać obsługę nowych potwierdzeń zasad do importowania <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> przez dodanie implementacji programu <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu do <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji na <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> wystąpienia. Alternatywnie można zarejestrować rozszerzenia importu zasad w pliku konfiguracyjnym aplikacji klienta.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu to implementacja <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> dołączone do klasy abstrakcyjnej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu importuje WSDL metadanych za pomocą dołączonego zasad, które są powiązane w <xref:System.ServiceModel.Description.MetadataSet> obiektu.  
  
 Można dodać obsługę importowanie rozszerzenia WSDL zaimplementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs, a następnie dodanie implementacji do <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> właściwości na Twojej <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> wystąpienia. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Można również ładować implementacje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejs zarejestrowany w pliku konfiguracyjnym aplikacji klienta.  
  
## <a name="dynamic-bindings"></a>Wiązania dynamicznego  
 Dynamiczne można zaktualizować powiązania, który jest używany do utworzenia kanału dla punktu końcowego w przypadku, gdy zmienia się powiązanie dla punktu końcowego lub chcesz utworzyć kanał do punktu końcowego, który używa ten sam kontrakt, ale ma inne powiązanie. Można użyć <xref:System.ServiceModel.Description.MetadataResolver> klasy statycznej, aby pobrać i zaimportować metadane w czasie wykonywania dla punktów końcowych usługi, które implementuje kontrakt określonych. Następnie można użyć importowanego <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> obiektów można utworzyć klienta lub kanału fabryki żądanego punktu końcowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description>  
 [Formaty metadanych](../../../../docs/framework/wcf/feature-details/metadata-formats.md)  
 [Eksportowanie i importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Pobieranie metadanych](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
