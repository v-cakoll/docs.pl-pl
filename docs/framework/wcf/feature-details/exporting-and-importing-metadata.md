---
title: Eksportowanie i importowanie metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: f07a1a10529aa1615bb00a0f3faeca9cb249aa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595534"
---
# <a name="exporting-and-importing-metadata"></a>Eksportowanie i importowanie metadanych
W programie Windows Communication Foundation (WCF) eksportowanie metadanych jest procesem opisywania punktów końcowych usługi i projekcją ich w równoległą, ustandaryzowaną reprezentacją, której klienci mogą używać w celu zrozumienia sposobu korzystania z usługi. Importowanie metadanych usługi to proces generowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień lub części z metadanych usługi.  
  
## <a name="exporting-metadata"></a>Eksportowanie metadanych  
 Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wystąpień, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.WsdlExporter>Typ to implementacja <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej dołączonej do WCF.  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType>Typ generuje metadane Web Services Description Language (WSDL) z dołączonymi wyrażeniami zasad hermetyzowanymi w <xref:System.ServiceModel.Description.MetadataSet> wystąpieniu. Można użyć wystąpienia, <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Aby iteracyjnie wyeksportować metadane dla <xref:System.ServiceModel.Description.ContractDescription> obiektów i <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów. Można również eksportować kolekcję <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów i kojarzyć je z określoną nazwą usługi.  
  
> [!NOTE]
> Można użyć `WsdlExporter` do eksportowania metadanych z `ContractDescription` wystąpień zawierających informacje o typie środowiska uruchomieniowego języka wspólnego (CLR), takie jak `ContractDescription` wystąpienie utworzone za pomocą `ContractDescription.GetContract` metody lub utworzone jako część `ServiceDescription` dla `ServiceHost` wystąpienia. Nie można użyć `WsdlExporter` do eksportowania metadanych z `ContractDescription` wystąpień importowanych z metadanych usługi lub skonstruowanych bez informacji o typie.  
  
## <a name="importing-metadata"></a>Importowanie metadanych  
  
### <a name="importing-wsdl-documents"></a>Importowanie dokumentów WSDL  
 Aby zaimportować metadane usługi w programie WCF, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Typ to implementacja <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej dołączonej do WCF. <xref:System.ServiceModel.Description.WsdlImporter>Typ importuje metadane WSDL z dołączonymi zasadami w <xref:System.ServiceModel.Description.MetadataSet> obiekcie.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ zapewnia kontrolę nad sposobem importowania metadanych. Możesz zaimportować wszystkie punkty końcowe, wszystkie powiązania lub wszystkie umowy. Wszystkie punkty końcowe skojarzone z określoną usługą WSDL, powiązaniem lub typem portu można zaimportować. Można również zaimportować punkt końcowy dla określonego portu WSDL, powiązania dla określonego powiązania WSDL lub kontraktu dla określonego typu portu WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Udostępnia również <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> Właściwość, która umożliwia określenie zestawu kontraktów, które nie muszą być importowane. <xref:System.ServiceModel.Description.WsdlImporter>Program używa kontraktów we <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> Właściwości zamiast importowania kontraktu o tej samej kwalifikowanej nazwie z metadanych.  
  
### <a name="importing-policies"></a>Importowanie zasad  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ zbiera wyrażenia zasad dołączone do tematów dotyczących komunikatów, operacji i zasad punktu końcowego, a następnie używa <xref:System.ServiceModel.Description.IPolicyImportExtension> implementacji w <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji w celu zaimportowania wyrażeń zasad.  
  
 Logika importowania zasad automatycznie obsługuje odwołania zasad do wyrażeń zasad w tym samym dokumencie WSDL i jest identyfikowany przy `wsu:Id` użyciu `xml:id` atrybutu or. Logika importowania zasad chroni aplikacje przed cyklicznymi odwołaniami do zasad przez ograniczenie rozmiaru wyrażenia zasad do 4096 węzłów, gdzie węzeł jest jednym z następujących elementów: `wsp:Policy` , `wsp:All` , `wsp:ExactlyOne` , `wsp:policyReference` .  
  
 Logika importowania zasad również automatycznie normalizuje wyrażenia zasad. Wyrażenia zasad zagnieżdżonych i `wsp:Optional` atrybut nie są znormalizowane. Liczba wykonanych operacji przetwarzania normalizacji jest ograniczona do 4096 kroków, gdzie każdy krok zwraca potwierdzenie zasad lub element podrzędny `wsp:ExactlyOne` elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ próbuje do 32 kombinacji alternatyw zasad dołączonych do różnych tematów zasad WSDL. Jeśli żadna kombinacja nie jest czysta, pierwsza kombinacja służy do konstruowania częściowego powiązania niestandardowego.  
  
## <a name="error-handling"></a>Obsługa błędów  
 Zarówno, <xref:System.ServiceModel.Description.MetadataExporter> jak i <xref:System.ServiceModel.Description.MetadataImporter> typy uwidaczniają `Errors` Właściwość, która może zawierać kolekcję komunikatów o błędach i ostrzeżeniach napotkanych w trakcie procesów eksportu i importu, które mogą być używane podczas implementowania narzędzi.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ zwykle zgłasza wyjątek dla wyjątku przechwytywanego podczas procesu importowania i dodaje odpowiedni błąd do jego `Errors` właściwości. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> Jednak metody,, i <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> nie generują tych wyjątków, dlatego należy sprawdzić `Errors` Właściwość, aby określić, czy występują problemy podczas wywoływania tych metod.  
  
 <xref:System.ServiceModel.Description.WsdlExporter>Typ ponownie generuje wszystkie wyjątki przechwycone podczas procesu eksportu. Te wyjątki nie są przechwytywane jako błędy we `Errors` właściwości. Gdy <xref:System.ServiceModel.Description.WsdlExporter> zgłasza wyjątek, jest w stanie nieprawidłowym i nie można go ponownie użyć. <xref:System.ServiceModel.Description.WsdlExporter>Program wykonuje Dodawanie ostrzeżeń do `Errors` właściwości, gdy nie można wyeksportować operacji, ponieważ używa ona wieloznacznych akcji i podczas napotkania zduplikowanych nazw powiązań.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Importowanie metadanych do punktów końcowych usług](how-to-import-metadata-into-service-endpoints.md)  
 Opisuje sposób importowania pobranych metadanych do obiektów opisu.  
  
 [Instrukcje: eksportowanie metadanych z punktów końcowych usług](how-to-export-metadata-from-service-endpoints.md)  
 Opisuje sposób eksportowania obiektów opisu do metadanych.  
  
 [Odwołania do elementu ServiceDescription i kodu WSDL](servicedescription-and-wsdl-reference.md)  
 Opisuje mapowanie między obiektami opisu a WSDL.  
  
 [Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Opisuje użycie programu Svcutil. exe do eksportowania metadanych dla usług, kontraktów i typów danych w skompilowanych zestawach.  
  
 [Odwołanie do schematu kontraktu danych](data-contract-schema-reference.md)  
 Opisuje podzestaw schematu XML (XSD) używany przez program <xref:System.Runtime.Serialization.DataContractSerializer> do opisywania typów wspólnych języka (CLR) dla serializacji XML.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Zobacz też

- [Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF](../extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../extending/importing-custom-metadata-for-a-wcf-extension.md)
