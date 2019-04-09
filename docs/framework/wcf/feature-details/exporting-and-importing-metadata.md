---
title: Eksportowanie i importowanie metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 39b964584cde42e6569da35f8653042f6d7432cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091944"
---
# <a name="exporting-and-importing-metadata"></a>Eksportowanie i importowanie metadanych
W Windows Communication Foundation (WCF), eksportowanie metadanych jest proces opisujące punkty końcowe usługi i wyświetlaniu je do reprezentacji równoległych, standardowe, której klienci mogą używać, aby zrozumieć sposób korzystania z usługi. Importowanie metadanych usługi jest proces generowania <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień lub składniki Report Part z metadanych usługi.  
  
## <a name="exporting-metadata"></a>Eksportowanie metadanych  
 Aby wyeksportować metadane z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wystąpień, korzystać z implementacji <xref:System.ServiceModel.Description.MetadataExporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.WsdlExporter> Typu jest implementacją <xref:System.ServiceModel.Description.MetadataExporter> abstrakcyjna klasa dołączone do programu WCF.  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Typu generuje metadane Web Services Description Language (WSDL) przy użyciu wyrażeń zasad dołączone w <xref:System.ServiceModel.Description.MetadataSet> wystąpienia. Możesz użyć <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> wystąpienia iteracyjne Eksportowanie metadanych dla <xref:System.ServiceModel.Description.ContractDescription> obiektów i <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów. Można także eksportować kolekcję <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów i skojarzyć je z nazwą określoną usługą.  
  
> [!NOTE]
>  Można używać tylko `WsdlExporter` Eksportowanie metadanych z `ContractDescription` wystąpień, które zawierają środowisko uruchomieniowe języka wspólnego (CLR) wpisz informacje, takie jak `ContractDescription` wystąpienia utworzone za pomocą `ContractDescription.GetContract` metody lub utworzonych jako część `ServiceDescription` Aby uzyskać `ServiceHost` wystąpienia. Nie można użyć `WsdlExporter` Eksportowanie metadanych z `ContractDescription` wystąpień zaimportowane z metadanych usługi lub skonstruowany bez informacji o typie.  
  
## <a name="importing-metadata"></a>Importowanie metadanych  
  
### <a name="importing-wsdl-documents"></a>Importowanie dokumenty WSDL  
 Aby zaimportować metadane usługi w programie WCF, należy korzystać z implementacji <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu jest implementacją <xref:System.ServiceModel.Description.MetadataImporter> abstrakcyjna klasa dołączone do programu WCF. <xref:System.ServiceModel.Description.WsdlImporter> Typ importu WSDL metadanych przy użyciu zasad dołączonych powiązane w <xref:System.ServiceModel.Description.MetadataSet> obiektu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu zapewnia kontrolę nad jak zaimportować metadane. Możesz zaimportować wszystkie punkty końcowe, wszystkie powiązania lub wszystkich umów. Można zaimportować wszystkich punktów końcowych skojarzonych z określonej usługi WSDL, powiązanie lub typ portu. Można również zaimportować punktu końcowego dla konkretnego portu WSDL, powiązanie dla określonych Powiązanie WSDL lub kontrakt dla określonego typu port WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Udostępnia również <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> właściwość, która pozwala użytkownikowi określić zestaw umowy, które nie muszą zostać zaimportowane. <xref:System.ServiceModel.Description.WsdlImporter> Używa kontraktów w <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> zamiast importowania kontrakt o takiej samej nazwie kwalifikowanej z metadanych właściwości.  
  
### <a name="importing-policies"></a>Importowanie zasad  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu zbiera wyrażeń zasad, w załączniku do wiadomości, operacji i zasad punktów końcowych przedmioty, a następnie używa <xref:System.ServiceModel.Description.IPolicyImportExtension> implementacji w <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekcji do zaimportowania wyrażeń zasad.  
  
 Logika importu zasad automatycznie obsługuje zasady odwołania do wyrażenia zasad, w tym samym dokumencie WSDL i jest identyfikowany za pomocą `wsu:Id` lub `xml:id` atrybutu. Logika importu zasad chroni aplikacji przed odwołania cykliczne zasad przez ograniczenie rozmiaru wyrażenie zasad do 4096 węzłów, w których węzeł jest jedną z następujących elementów: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 Logika importu zasad normalizuje również automatycznie wyrażeń zasad. Zagnieżdżone wyrażenia zasad i `wsp:Optional` atrybut nie jest znormalizować. Ilość normalizacji przetwarzania wykonywane jest ograniczona do 4096 kroków, w której każdy krok daje asercję zasad lub element podrzędny `wsp:ExactlyOne` elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu próbuje maksymalnie 32 kombinacji zasad alternatywnych dołączone do różnych tematów zasad WSDL. Jeśli połączenie nie importuje nie pozostawia żadnych śladów, pierwsza kombinacja jest używany do tworzenia częściowe niestandardowego powiązania.  
  
## <a name="error-handling"></a>Obsługa błędów  
 Zarówno <xref:System.ServiceModel.Description.MetadataExporter> i <xref:System.ServiceModel.Description.MetadataImporter> typy ujawnić `Errors` właściwości zawierające kolekcję o błędach i komunikaty ostrzegawcze, napotkała w procesach eksportu i importu, odpowiednio, które mogą być używane w przypadku wdrażania narzędzia.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu ogólnie zgłasza wyjątek, wyjątek zgłoszony podczas procesu importowania i dodaje odpowiednie błąd do jego `Errors` właściwości. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, I <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> metod, jednak nie zgłaszają wyjątków tych wyjątków, dlatego należy sprawdzić `Errors` właściwości w celu określenia, czy wszelkie problemy wystąpił podczas wywołania tych metod.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typu ponownie zgłasza wyjątki przechwytywane podczas procesu eksportowania. Wyjątki te nie są przechwytywane jako błędy w `Errors` właściwości. Raz <xref:System.ServiceModel.Description.WsdlExporter> zgłasza wyjątek, który, jest w nieprawidłowym stanie i nie można użyć ponownie. <xref:System.ServiceModel.Description.WsdlExporter> Dodaj ostrzeżeń do jego `Errors` właściwość podczas operacji nie można wyeksportować, ponieważ korzysta ona z symboli wieloznacznych, akcje i kiedy występują zduplikowane powiązanie nazwy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: importowanie metadanych do punktów końcowych usług](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 W tym artykule opisano, jak zaimportować pobrany metadanych do opisu obiektów.  
  
 [Instrukcje: eksportowanie metadanych z punktów końcowych usług](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Opisuje sposób eksportowania obiektów opis do metadanych.  
  
 [Odwołania do elementu ServiceDescription i kodu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Opisuje mapowanie między obiektami opis i WSDL.  
  
 [Instrukcje: eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 W tym artykule opisano użycie programu Svcutil.exe do wyeksportowania metadanych dla usługi, kontrakty i typów danych w skompilowanych zestawach.  
  
 [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 W tym artykule opisano podzbioru elementu schematu XML (XSD) używane przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisania języka wspólnego środowiska wykonawczego (języka wspólnego CLR) typy serializacji XML.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Zobacz także

- [Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
