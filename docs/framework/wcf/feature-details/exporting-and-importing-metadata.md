---
title: Eksportowanie i importowanie metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 692382de81459ad52d306ca7fd05546b4e36294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963662"
---
# <a name="exporting-and-importing-metadata"></a>Eksportowanie i importowanie metadanych
W programie Windows Communication Foundation (WCF) eksportowanie metadanych jest procesem opisywania punktów końcowych usługi i projekcją ich w równoległą, ustandaryzowaną reprezentacją, której klienci mogą używać w celu zrozumienia sposobu korzystania z usługi. Importowanie metadanych usługi to proces generowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień lub części z metadanych usługi.  
  
## <a name="exporting-metadata"></a>Eksportowanie metadanych  
 Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wystąpień, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. Typ to implementacja <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej dołączonej do WCF. <xref:System.ServiceModel.Description.WsdlExporter>  
  
 Typ generuje metadane Web Services Description Language (WSDL) z dołączonymi wyrażeniami zasad hermetyzowanymi <xref:System.ServiceModel.Description.MetadataSet> w wystąpieniu. <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Można użyć <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> wystąpienia, aby iteracyjnie wyeksportować metadane dla <xref:System.ServiceModel.Description.ContractDescription> obiektów i <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów. Można również eksportować kolekcję <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów i kojarzyć je z określoną nazwą usługi.  
  
> [!NOTE]
> Można `WsdlExporter` użyć do eksportowania metadanych z `ContractDescription` wystąpień zawierających `ContractDescription` informacje o typie środowiska uruchomieniowego języka wspólnego (CLR), takie jak wystąpienie utworzone za pomocą `ContractDescription.GetContract` metody lub utworzone jako część `ServiceDescription` `ServiceHost` dla wystąpienia. Nie można użyć `WsdlExporter` do eksportowania metadanych z `ContractDescription` wystąpień importowanych z metadanych usługi lub skonstruowanych bez informacji o typie.  
  
## <a name="importing-metadata"></a>Importowanie metadanych  
  
### <a name="importing-wsdl-documents"></a>Importowanie dokumentów WSDL  
 Aby zaimportować metadane usługi w programie WCF, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. Typ to implementacja <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej dołączonej do WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ importuje metadane WSDL z dołączonymi zasadami <xref:System.ServiceModel.Description.MetadataSet> w obiekcie. <xref:System.ServiceModel.Description.WsdlImporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ zapewnia kontrolę nad sposobem importowania metadanych. Możesz zaimportować wszystkie punkty końcowe, wszystkie powiązania lub wszystkie umowy. Wszystkie punkty końcowe skojarzone z określoną usługą WSDL, powiązaniem lub typem portu można zaimportować. Można również zaimportować punkt końcowy dla określonego portu WSDL, powiązania dla określonego powiązania WSDL lub kontraktu dla określonego typu portu WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Udostępniarównieżwłaściwość,któraumożliwiaokreśleniezestawukontraktów,które<xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> nie muszą być importowane. Program używa kontraktów we właściwości zamiast importowania kontraktu o tej samej kwalifikowanej nazwie z metadanych. <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> <xref:System.ServiceModel.Description.WsdlImporter>  
  
### <a name="importing-policies"></a>Importowanie zasad  
 Typ zbiera wyrażenia zasad dołączone do tematów dotyczących komunikatów, operacji i zasad punktu końcowego, a następnie <xref:System.ServiceModel.Description.IPolicyImportExtension> używa implementacji w <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji w celu zaimportowania wyrażeń zasad. <xref:System.ServiceModel.Description.WsdlImporter>  
  
 Logika importowania zasad automatycznie obsługuje odwołania zasad do wyrażeń zasad w tym samym dokumencie WSDL i jest identyfikowany przy `wsu:Id` użyciu `xml:id` atrybutu or. Logika importowania zasad chroni aplikacje przed cyklicznymi odwołaniami do zasad przez ograniczenie rozmiaru wyrażenia zasad do 4096 węzłów, gdzie węzeł jest jednym z następujących elementów `wsp:Policy`:, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 Logika importowania zasad również automatycznie normalizuje wyrażenia zasad. Wyrażenia zasad zagnieżdżonych i `wsp:Optional` atrybut nie są znormalizowane. Liczba wykonanych operacji przetwarzania normalizacji jest ograniczona do 4096 kroków, gdzie każdy krok zwraca potwierdzenie zasad lub element `wsp:ExactlyOne` podrzędny elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ próbuje do 32 kombinacji alternatyw zasad dołączonych do różnych tematów zasad WSDL. Jeśli żadna kombinacja nie jest czysta, pierwsza kombinacja służy do konstruowania częściowego powiązania niestandardowego.  
  
## <a name="error-handling"></a>Obsługa błędów  
 Zarówno, <xref:System.ServiceModel.Description.MetadataExporter> `Errors` jak i typy uwidaczniają właściwość, która może zawierać kolekcję komunikatów o błędach i ostrzeżeniach napotkanych w trakcie procesów eksportu i importu, które mogą być używane podczas implementowania narzędzi. <xref:System.ServiceModel.Description.MetadataImporter>  
  
 Typ zwykle zgłasza wyjątek dla wyjątku przechwytywanego podczas procesu importowania i dodaje odpowiedni błąd do jego `Errors` właściwości. <xref:System.ServiceModel.Description.WsdlImporter> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>Jednak metody `Errors` , ,<xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> i<xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> nie generują tych wyjątków, dlatego należy sprawdzić właściwość, aby określić, czy występują problemy podczas wywoływania tych metod. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typ ponownie generuje wszystkie wyjątki przechwycone podczas procesu eksportu. Te wyjątki nie są przechwytywane jako błędy we `Errors` właściwości. <xref:System.ServiceModel.Description.WsdlExporter> Gdy zgłasza wyjątek, jest w stanie nieprawidłowym i nie można go ponownie użyć. Program <xref:System.ServiceModel.Description.WsdlExporter> wykonuje Dodawanie ostrzeżeń `Errors` do właściwości, gdy nie można wyeksportować operacji, ponieważ używa ona wieloznacznych akcji i podczas napotkania zduplikowanych nazw powiązań.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Importowanie metadanych do punktów końcowych usługi](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Opisuje sposób importowania pobranych metadanych do obiektów opisu.  
  
 [Instrukcje: Eksportowanie metadanych z punktów końcowych usługi](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Opisuje sposób eksportowania obiektów opisu do metadanych.  
  
 [Odwołania do elementu ServiceDescription i kodu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Opisuje mapowanie między obiektami opisu a WSDL.  
  
 [Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil. exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Opisuje użycie programu Svcutil. exe do eksportowania metadanych dla usług, kontraktów i typów danych w skompilowanych zestawach.  
  
 [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Opisuje podzestaw schematu XML (XSD) używany przez <xref:System.Runtime.Serialization.DataContractSerializer> program do opisywania typów wspólnych języka (CLR) dla serializacji XML.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Zobacz także

- [Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
