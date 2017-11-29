---
title: Eksportowanie i importowanie metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6231d6e4b6562aafbb5b6bd88b65b66f44469023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exporting-and-importing-metadata"></a>Eksportowanie i importowanie metadanych
W [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], eksportowanie metadanych jest proces opisujące punktów końcowych usługi i projekcji ich reprezentację równoległe, standardowe, której klienci mogą używać, aby zrozumieć sposób korzystania z usługi. Importowanie metadanych usługi to proces generowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień lub części z metadanych usługi.  
  
## <a name="exporting-metadata"></a>Eksportowanie metadanych  
 Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wystąpień, korzystać z implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.WsdlExporter> Typu to implementacja <xref:System.ServiceModel.Description.MetadataExporter> dołączone do klasy abstrakcyjnej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Typu generuje metadane Web Services Description Language (WSDL) za pomocą wyrażeń zasady dołączone hermetyzowane w <xref:System.ServiceModel.Description.MetadataSet> wystąpienia. Można użyć <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> wystąpienia wielokrotnie powtarzane eksportu metadanych <xref:System.ServiceModel.Description.ContractDescription> obiektów i <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów. Można również wyeksportować Kolekcja <xref:System.ServiceModel.Description.ServiceEndpoint> obiekty i kojarzyć je przy użyciu nazwy określonej usługi.  
  
> [!NOTE]
>  Można używać tylko `WsdlExporter` Eksportowanie metadanych z `ContractDescription` wystąpień, które zawierają środowisko uruchomieniowe języka wspólnego (CLR) wpisz informacje, takie jak `ContractDescription` wystąpienia utworzone za pomocą `ContractDescription.GetContract` metody lub utworzone jako część `ServiceDescription` Aby uzyskać `ServiceHost` wystąpienia. Nie można użyć `WsdlExporter` Eksportowanie metadanych z `ContractDescription` wystąpień zaimportowane z metadanych usługi lub skonstruowane bez informacji o typie.  
  
## <a name="importing-metadata"></a>Importowanie metadanych  
  
### <a name="importing-wsdl-documents"></a>Importowanie dokumentów WSDL  
 Aby zaimportować metadane usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], korzystać z implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu to implementacja <xref:System.ServiceModel.Description.MetadataImporter> dołączone do klasy abstrakcyjnej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter> Typu imports WSDL metadanych za pomocą dołączonego zasady dołączone do <xref:System.ServiceModel.Description.MetadataSet> obiektu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu umożliwia kontrolowanie sposobu zaimportować metadane. Możesz zaimportować wszystkie punkty końcowe, wszystkie powiązania lub wszystkich umów. Możesz zaimportować wszystkie punkty końcowe skojarzone z określoną usługą WSDL, powiązanie lub typ portu. Możesz również zaimportować punkt końcowy dla określonego portu WSDL, powiązanie dla określonego powiązania WSDL lub kontrakt dla określonego typu portu WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Udostępnia również <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> właściwość, która służy do określenia zestawu umów, które nie są do zaimportowania. <xref:System.ServiceModel.Description.WsdlImporter> Używa kontrakty w <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> zamiast importowanie kontraktu o takiej samej nazwie kwalifikowanej z metadanych właściwości.  
  
### <a name="importing-policies"></a>Importowanie zasad  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu zbiera wyrażenia zasad, dołączony do wiadomości, operację, i tematy zasady dla punktu końcowego, a następnie używa <xref:System.ServiceModel.Description.IPolicyImportExtension> implementacje w <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji do zaimportowania wyrażenie zasad.  
  
 Logika importu zasad automatycznie obsługuje zasady odwołania do wyrażenia zasad, w tym samym dokumencie WSDL i o `wsu:Id` lub `xml:id` atrybutu. Logika importu zasad chroni aplikacje przed odwołania cykliczne zasad przez ograniczenie rozmiaru wyrażenie zasad do 4096 węzłów, gdy węzeł ma jeden z następujących elementów: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 Logika importu zasad normalizuje automatycznie wyrażenie zasad. Zagnieżdżone wyrażenia zasad i `wsp:Optional` nie są znormalizować atrybutu. Ilość przetwarzanych danych normalizacji wykonywane jest ograniczona do 4096 kroków, w którym każdy krok daje potwierdzenia zasad lub elementu podrzędnego `wsp:ExactlyOne` elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu próbuje maksymalnie 32 kombinacje zasad alternatywnych dołączone do różnych tematów zasad WSDL. Jeśli połączenie nie importuje prawidłowo, pierwsza kombinacja służy do utworzenia częściowego wiązania niestandardowego.  
  
## <a name="error-handling"></a>Obsługa błędów  
 Zarówno <xref:System.ServiceModel.Description.MetadataExporter> i <xref:System.ServiceModel.Description.MetadataImporter> ujawnia typy `Errors` właściwości zawierających kolekcji o błędach i komunikaty ostrzegawcze odpowiednio napotkał podczas procesu eksportowania i importowania, które mogą być używane podczas implementowania narzędzia.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu zazwyczaj zgłasza wyjątek wyjątek zgłoszony podczas procesu importowania i dodaje odpowiednich błąd do jego `Errors` właściwości. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, I <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> metod, jednak nie zgłaszają te wyjątki, dlatego należy sprawdzić `Errors` właściwości do określenia, czy problemy wystąpiły podczas wywołania tych metod.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typu ponownie zgłasza wszelkie wyjątki przechwycono podczas procesu eksportowania. Wyjątki te nie są przechwytywane jako błędy w `Errors` właściwości. Raz <xref:System.ServiceModel.Description.WsdlExporter> zgłasza wyjątek, który występuje, jest stan i nie można użyć ponownie. <xref:System.ServiceModel.Description.WsdlExporter> Dodać ostrzeżenia, aby jego `Errors` właściwość podczas operacji nie można wyeksportować, ponieważ użyto akcji symbolu wieloznacznego oraz gdy występują zduplikowane powiązanie nazwy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Importowanie metadanych do punktów końcowych usług](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Opisuje sposób importowania metadanych pobranych do opisu obiektów.  
  
 [Porady: Eksportowanie metadanych z punktów końcowych usług](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Opisuje sposób eksportowania obiektów opis w metadanych.  
  
 [ServiceDescription i kodu WSDL odwołania](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Opisuje mapowanie między obiektami opis i WSDL.  
  
 [Porady: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Opisuje Svcutil.exe do wyeksportowania metadanych dla usługi, kontrakty i typów danych w zestawach skompilowany.  
  
 [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 W tym artykule opisano podzestawu elementu schematu XML (XSD) używany przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisywania wspólnego języka środowiska wykonawczego (języka wspólnego CLR) typy serializacji XML.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
