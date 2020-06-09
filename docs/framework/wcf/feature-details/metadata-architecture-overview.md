---
title: Przegląd architektury metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: a6bd41fa5aed4c2a22ee7c72087e2da0d7e4ea17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598856"
---
# <a name="metadata-architecture-overview"></a>Przegląd architektury metadanych
Windows Communication Foundation (WCF) zawiera rozbudowaną infrastrukturę do eksportowania, publikowania, pobierania i importowania metadanych usługi. Usługi WCF używają metadanych do opisywania sposobu współdziałania z punktami końcowymi usługi, dzięki czemu narzędzia, takie jak Svcutil. exe, mogą automatycznie generować kod klienta na potrzeby uzyskiwania dostępu do usługi.  
  
 Większość typów tworzących infrastrukturę metadanych programu WCF znajduje się w <xref:System.ServiceModel.Description> przestrzeni nazw.  
  
 Funkcja WCF używa <xref:System.ServiceModel.Description.ServiceEndpoint> klasy do opisywania punktów końcowych w usłudze. Za pomocą programu WCF można generować metadane dla punktów końcowych usługi lub zaimportować metadane usługi w celu wygenerowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień.  
  
 Funkcja WCF reprezentuje metadane dla usługi jako wystąpienie <xref:System.ServiceModel.Description.MetadataSet> typu, struktury, która jest silnie związana z formatem serializacji metadanych zdefiniowanym w usłudze WS-MetadataExchange. <xref:System.ServiceModel.Description.MetadataSet>Typ pakietuje rzeczywiste metadane usługi, takie jak dokumenty Web Services Description Language (WSDL), dokumenty schematu XML lub wyrażenia WS-Policy jako kolekcje <xref:System.ServiceModel.Description.MetadataSection> wystąpień. Każde <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> wystąpienie zawiera konkretny dialekt metadanych i identyfikator. Element <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> może zawierać następujące elementy w swojej <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> Właściwości:  
  
- Metadane pierwotne.  
  
- <xref:System.ServiceModel.Description.MetadataReference>Wystąpienie.  
  
- <xref:System.ServiceModel.Description.MetadataLocation>Wystąpienie.  
  
 <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType>Wystąpienia wskazują na inny punkt końcowy wymiany metadanych (Mex) i <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> wystąpienia wskazują na dokument metadanych przy użyciu adresu URL protokołu HTTP. WCF obsługuje używanie dokumentów WSDL do opisywania punktów końcowych usługi, kontraktów usług, powiązań, wzorców wymiany komunikatów, komunikatów i komunikatów o błędach wdrożonych przez usługę. Typy danych używane przez usługę są opisane w dokumentach WSDL przy użyciu schematu XML. Aby uzyskać więcej informacji, zobacz [Importowanie i eksportowanie schematu](schema-import-and-export.md). Można użyć programu WCF do eksportowania i importowania rozszerzeń WSDL do zachowania usługi, zachowań kontraktu i elementów powiązania, które rozszerzają funkcjonalność usługi. Aby uzyskać więcej informacji, zobacz [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Eksportowanie metadanych usługi  
 W programie WCF *Eksport metadanych* jest procesem opisywania punktów końcowych usługi i umieszczania ich w równoległej, znormalizowanej reprezentacji, z której klienci mogą zrozumieć, jak korzystać z usługi. Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Implementacja generuje metadane, które są hermetyzowane w <xref:System.ServiceModel.Description.MetadataSet> wystąpieniu.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Klasa zawiera strukturę służącą do generowania wyrażeń zasad, które opisują możliwości i wymagania powiązania punktu końcowego oraz skojarzone z nim operacje, komunikaty i błędy. Te wyrażenia zasad są przechwytywane w <xref:System.ServiceModel.Description.PolicyConversionContext> wystąpieniu. <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Implementacja może następnie dołączyć te wyrażenia zasad do generowanych metadanych.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Wywołania każdej <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> , które implementują <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejs w powiązaniu elementu <xref:System.ServiceModel.Description.ServiceEndpoint> podczas generowania <xref:System.ServiceModel.Description.PolicyConversionContext> obiektu do <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> użycia przez implementację. Nowe potwierdzenia zasad można wyeksportować, implementując <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejs w niestandardowych implementacjach <xref:System.ServiceModel.Channels.BindingElement> typu.  
  
 <xref:System.ServiceModel.Description.WsdlExporter>Typ to implementacja <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> klasy abstrakcyjnej dołączonej do WCF. <xref:System.ServiceModel.Description.WsdlExporter>Typ generuje metadane WSDL z dołączonymi wyrażeniami zasad.  
  
 Aby wyeksportować niestandardowe metadane WSDL lub rozszerzenia WSDL dla zachowań punktów końcowych, zachowań kontraktu lub elementów powiązania w punkcie końcowym usługi, można zaimplementować <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejs. <xref:System.ServiceModel.Description.WsdlExporter>Przegląda <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienie dla elementów powiązania, zachowań operacji, zachowań kontraktu i zachowań punktów końcowych, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejs podczas generowania dokumentu WSDL.  
  
## <a name="publishing-service-metadata"></a>Publikowanie metadanych usługi  
 Usługi WCF publikują metadane, ujawniając jeden lub więcej punktów końcowych metadanych. Publikowanie metadanych usługi sprawia, że metadane usługi są dostępne przy użyciu standardowych protokołów, takich jak żądania MEX i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, które mają adres, powiązanie i kontrakt. Punkty końcowe metadanych można dodać do hosta usługi w konfiguracji lub w kodzie.  
  
 Aby opublikować punkty końcowe metadanych dla usługi WCF, należy najpierw dodać wystąpienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowania usługi do usługi. Dodanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpienia do usługi rozszerza swoją usługę z możliwością publikowania metadanych przez ujawnienie co najmniej jednego punktu końcowego metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowania usługi możesz udostępnić punkty końcowe metadanych, które obsługują protokół MEX lub punkty końcowe metadanych odpowiadające na żądania HTTP/GET.  
  
 Aby dodać punkty końcowe metadanych używające protokołu MEX, Dodaj punkty końcowe usługi do hosta usługi, które korzystają z kontraktu usługi o nazwie kontraktem IMetadataExchange. WCF definiuje <xref:System.ServiceModel.Description.IMetadataExchange> interfejs, który ma tę nazwę kontraktu usługi. Punkty końcowe usługi WS-MetadataExchange lub punkty końcowe MEX mogą korzystać z jednego z czterech domyślnych powiązań udostępnianych przez statyczne metody fabryki w <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasie w celu dopasowania do domyślnych powiązań używanych przez narzędzia WCF, takich jak Svcutil. exe. Możesz również skonfigurować punkty końcowe metadanych MEX przy użyciu niestandardowego powiązania.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Używa <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> do eksportowania metadanych dla wszystkich punktów końcowych usługi w usłudze. Aby uzyskać więcej informacji na temat eksportowania metadanych z usługi, zobacz [Eksportowanie i Importowanie metadanych](exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Rozszerza hosta usługi przez dodanie <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienia jako rozszerzenia do hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType>Zawiera implementację protokołów publikowania metadanych. Możesz również użyć, <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Aby pobrać metadane usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> właściwości.  
  
> [!CAUTION]
> Jeśli dodasz punkt końcowy MEX w pliku konfiguracji aplikacji, a następnie spróbujesz dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do hosta usługi w kodzie, otrzymujesz następujący wyjątek:  
>
> System. InvalidOperationException: nie można odnaleźć nazwy kontraktu "kontraktem IMetadataExchange" na liście kontraktów wdrożonych przez usługę Service1. Dodaj ServiceMetadataBehavior do pliku konfiguracji lub do ServiceHost bezpośrednio, aby włączyć obsługę tego kontraktu.  
>
> Ten problem można obejść przez dodanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w pliku konfiguracji lub dodanie punktu końcowego i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kodu.  
>
> Przykład dodawania <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w pliku konfiguracji aplikacji można znaleźć w [wprowadzenie](../samples/getting-started-sample.md). Aby zapoznać się z przykładem dodawania <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kodu, zapoznaj się z przykładem [samoobsługi](../samples/self-host.md) .  

> [!CAUTION]
> Podczas publikowania metadanych dla usługi, która uwidacznia dwie różne kontrakty usługi, w których każda z nich zawiera operację o tej samej nazwie, zgłaszany jest wyjątek. Na przykład jeśli masz usługę, która ujawnia kontrakt usługi o nazwie ICarService, który ma operację get (samochód c), a ta sama usługa ujawnia kontrakt usługi o nazwie IBookService, który ma operację get (Book b), zgłaszany jest wyjątek lub komunikat o błędzie jest wyświetlany podczas generowania metadanych usługi. Aby obejść ten problem, wykonaj jedną z następujących czynności:  
>
> - Zmień nazwę jednej z operacji.
> - Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> inną nazwę.  
> - Ustaw jedną z przestrzeni nazw operacji na inną przestrzeń nazw przy użyciu <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
## <a name="retrieving-service-metadata"></a>Pobieranie metadanych usługi  
 Program WCF może pobrać metadane usługi przy użyciu standardowych protokołów, takich jak WS-MetadataExchange i HTTP. Oba te protokoły są obsługiwane przez <xref:System.ServiceModel.Description.MetadataExchangeClient> Typ. Pobieranie metadanych usługi przy użyciu <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu przez podanie adresu i opcjonalnego powiązania. Powiązanie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienie może być jednym z domyślnych powiązań z <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy statycznej, powiązanie dostarczone przez użytkownika lub powiązanie załadowane z konfiguracji punktu końcowego dla `IMetadataExchange` kontraktu. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Może również rozpoznać odwołania do adresów URL protokołu HTTP w celu uzyskania metadanych przy użyciu <xref:System.Net.HttpWebRequest> typu.  
  
 Domyślnie <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienie jest powiązane z pojedynczym <xref:System.ServiceModel.Channels.ChannelFactoryBase> wystąpieniem. Można zmienić lub zastąpić <xref:System.ServiceModel.Channels.ChannelFactoryBase> wystąpienie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> metody wirtualnej. Podobnie można zmienić lub zastąpić <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> wystąpienie używane przez element, <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Aby wykonać żądania HTTP/GET przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> metody wirtualnej.  
  
 Metadane usługi można pobrać przy użyciu protokołu WS-MetadataExchange lub HTTP/GET przy użyciu narzędzia Svcutil. exe i przekazując przełącznik **/target: Metadata** i adres. Svcutil. exe pobiera metadane pod określonym adresem i zapisuje pliki na dysku. Svcutil. exe używa <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia wewnętrznie i ładuje konfigurację punktu końcowego MEX (z pliku konfiguracyjnego aplikacji), którego nazwa pasuje do schematu adresu przesłanego do Svcutil. exe, jeśli taki istnieje. W przeciwnym razie Svcutil. exe domyślnie używa jednego ze powiązań zdefiniowanych przez <xref:System.ServiceModel.Description.MetadataExchangeBindings> Typ fabryki statycznej.  
  
## <a name="importing-service-metadata"></a>Importowanie metadanych usługi  
 W programie WCF Importowanie metadanych jest procesem generowania abstrakcyjnej reprezentacji usługi lub jej części składowych z metadanych. Na przykład WCF może importować <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia, <xref:System.ServiceModel.Channels.Binding> wystąpienia lub <xref:System.ServiceModel.Description.ContractDescription> wystąpienia z dokumentu WSDL dla usługi. Aby zaimportować metadane usługi w programie WCF, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. Typy, które pochodzą z <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasy implementują obsługę importowania formatów metadanych, które korzystają z logiki importu WS-Policy w programie WCF.  
  
 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>Implementacja zbiera wyrażenia zasad dołączone do metadanych usługi w <xref:System.ServiceModel.Description.PolicyConversionContext> obiekcie. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>Następnie przetwarza zasady w ramach importowania metadanych, wywołując implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu we <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> właściwości.  
  
 Można dodać obsługę importowania nowych potwierdzeń zasad do a <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> przez dodanie własnej implementacji <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu do <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji w <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> wystąpieniu. Alternatywnie możesz zarejestrować rozszerzenie import zasad w pliku konfiguracji aplikacji klienckiej.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Typ to implementacja <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasy abstrakcyjnej dołączonej do WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Typ importuje metadane WSDL z dołączonymi zasadami, które są powiązane z <xref:System.ServiceModel.Description.MetadataSet> obiektem.  
  
 Można dodać obsługę importowania rozszerzeń WSDL, implementując <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs, a następnie dodając implementację do <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> właściwości w <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> wystąpieniu. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Może również ładować implementacje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu zarejestrowanego w pliku konfiguracyjnym aplikacji klienckiej.  
  
## <a name="dynamic-bindings"></a>Powiązania dynamiczne  
 Można dynamicznie aktualizować powiązanie, które służy do tworzenia kanału w punkcie końcowym usługi w przypadku zmiany powiązania dla punktu końcowego lub chcesz utworzyć kanał do punktu końcowego, który używa tego samego kontraktu, ale ma inne powiązanie. Można użyć <xref:System.ServiceModel.Description.MetadataResolver> klasy statycznej do pobierania i importowania metadanych w czasie wykonywania dla punktów końcowych usługi, które implementują określony kontrakt. Następnie można użyć zaimportowanych <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> obiektów do utworzenia fabryki klienta lub kanału do żądanego punktu końcowego.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description>
- [Formaty metadanych](metadata-formats.md)
- [Eksportowanie i importowanie metadanych](exporting-and-importing-metadata.md)
- [Publikowanie metadanych](publishing-metadata.md)
- [Pobieranie metadanych](retrieving-metadata.md)
- [Używanie metadanych](using-metadata.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](security-considerations-with-metadata.md)
- [Rozszerzanie systemu metadanych](../extending/extending-the-metadata-system.md)
