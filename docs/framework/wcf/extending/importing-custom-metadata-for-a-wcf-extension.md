---
title: Importowanie niestandardowych metadanych dla rozszerzenia WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 36bc4c9291b60ae5ad6e9964c361ed9e7a7c8317
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963497"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Importowanie niestandardowych metadanych dla rozszerzenia WCF
W programie Windows Communication Foundation (WCF) Importowanie metadanych jest procesem generowania abstrakcyjnej reprezentacji usługi lub jej części składowych z metadanych. Na przykład WCF może importować <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia, <xref:System.ServiceModel.Channels.Binding> wystąpienia lub <xref:System.ServiceModel.Description.ContractDescription> wystąpienia z dokumentu WSDL dla usługi. Aby zaimportować metadane usługi w programie WCF, należy użyć implementacji <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasy abstrakcyjnej. Typy, które pochodzą z <xref:System.ServiceModel.Description.MetadataImporter> klasy implementują obsługę importowania formatów metadanych, które korzystają z logiki importu WS-Policy w programie WCF.  
  
 Metadane niestandardowe składają się z elementów XML, których nie można zaimportować przez importerów metadanych dostarczonych przez system. Zwykle dotyczy to niestandardowych rozszerzeń WSDL i potwierdzeń zasad niestandardowych.  
  
 W tej sekcji opisano sposób importowania niestandardowych rozszerzeń WSDL i potwierdzeń zasad. Nie koncentruje się na samym procesie importowania. Aby uzyskać więcej informacji na temat używania typów eksportujących i importowanych metadanych niezależnie od tego, czy metadane są niestandardowe czy obsługiwane przez system, zobacz [Eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Omówienie  
 Typ to implementacja <xref:System.ServiceModel.Description.MetadataImporter> klasy abstrakcyjnej dołączonej do WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ importuje metadane WSDL z dołączonymi zasadami, które są powiązane <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> z obiektem. <xref:System.ServiceModel.Description.WsdlImporter> Potwierdzenia zasad i rozszerzenia WSDL, które nie są rozpoznawane przez importerów domyślnie, są przesyłane do wszelkich zarejestrowanych zasad niestandardowych i importerów WSDL do importowania. Zwykle importerzy są wdrażani w celu obsługi elementów powiązania zdefiniowanych przez użytkownika lub modyfikacji zaimportowanego kontraktu.  
  
 W tej sekcji opisano:  
  
1. Jak zaimplementować i korzystać z <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu, który udostępnia dane WSDL niestandardowym importerom przed generowaniem opisów i generowaniem kodu. Tego interfejsu można użyć do sprawdzenia lub modyfikacji typów opisu i kompilowania kodu za pomocą danego zestawu metadanych.  
  
2. Jak zaimplementować i korzystać z <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu, który udostępnia potwierdzenia zasad przed wygenerowaniem obiektów opisu. Tego interfejsu można użyć do sprawdzenia lub zmodyfikowania powiązania lub kontraktu na podstawie pobranych zasad.  
  
 Aby uzyskać więcej informacji na temat eksportowania niestandardowych zatwierdzeń WSDL i zasad, zobacz [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Importowanie niestandardowych rozszerzeń WSDL  
 Aby dodać obsługę importowania rozszerzeń WSDL, zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs, a następnie Dodaj implementację <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> do właściwości. Może również ładować implementacje <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejsu zarejestrowanego w pliku konfiguracyjnym aplikacji. <xref:System.ServiceModel.Description.WsdlImporter> Należy zauważyć, że liczba importerów WSDL jest domyślnie rejestrowana, a kolejność zarejestrowanych importerów WSDL jest istotna.  
  
 Gdy niestandardowy importer WSDL jest ładowany i używany przez <xref:System.ServiceModel.Description.WsdlImporter>, <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> najpierw wywoływana jest metoda, która umożliwia modyfikację metadanych przed procesem importu. Następnie umowy są importowane po wywołaniu metody, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> aby umożliwić modyfikację kontraktów zaimportowanych z metadanych. Na koniec Metoda jest wywoływana w celu włączenia modyfikacji importowanych punktów końcowych. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A>  
  
 Aby uzyskać więcej informacji, zobacz [jak: Importuj niestandardowe WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Importowanie potwierdzeń zasad niestandardowych  
 Typ i narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) automatycznie obsługują przetwarzanie różnych typów potwierdzeń zasad w wyrażeniach zasad dołączonych do dokumentów WSDL. <xref:System.ServiceModel.Description.WsdlImporter> Te narzędzia zbierają, normalizuje i scalają wyrażenia zasad dołączone do powiązań WSDL i portów WSDL.  
  
 Aby dodać obsługę importowania potwierdzeń zasad niestandardowych, zaimplementuj <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejs, a następnie Dodaj implementację <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> do właściwości. Może również ładować implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu zarejestrowanego w pliku konfiguracyjnym aplikacji. <xref:System.ServiceModel.Description.MetadataImporter> Należy zauważyć, że liczba importerów zasad jest domyślnie rejestrowana i kolejność zarejestrowanego importera zasad jest istotna.  
  
 System metadanych wielokrotnie wywołuje <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metodę we wszystkich zarejestrowanej rozszerzeniu importowania zasad dla każdej kombinacji alternatyw zasad dołączonych do tematów dotyczących wiadomości, operacji i zasad punktu końcowego. Podczas importowania portu WSDL zasady dołączone do portu i odpowiedniego powiązania WSDL są scalane przed wywołaniem ich w rozszerzeniach importu zasad. Alternatywy zasad są udostępniane za pomocą <xref:System.ServiceModel.Description.PolicyConversionContext> obiektów AS. <xref:System.ServiceModel.Description.PolicyAssertionCollection> Każda <xref:System.ServiceModel.Description.PolicyAssertionCollection> z nich jest kolekcją potwierdzeń zasad <xref:System.Xml.XmlElement> reprezentowanych przez obiekty.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> Właściwości i<xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> obiektu uwidaczniają<xref:System.ServiceModel.Description.ContractDescription> obiekty i<xref:System.ServiceModel.Channels.BindingElement> , które zostały zaimportowane z WSDL. <xref:System.ServiceModel.Description.PolicyConversionContext> Rozszerzenia importowania zasad przetwórz potwierdzenia zasad, wyszukując wystąpienia określonego typu potwierdzenia zasad, wprowadzając odpowiednie zmiany <xref:System.ServiceModel.Description.ContractDescription> w obiektach lub <xref:System.ServiceModel.Channels.BindingElement> , a następnie usuwając potwierdzenia zasad z odpowiednich <xref:System.ServiceModel.Description.PolicyAssertionCollection> wystąpienie.  
  
 `wsp:Optional` Atrybut i zagnieżdżone wyrażenia zasad nie są znormalizowane, dlatego rozszerzenia importu zasad muszą obsługiwać te konstrukcje zasad. Ponadto rozszerzenia importowania zasad mogą być wywoływane wiele razy z tymi samymi <xref:System.ServiceModel.Description.ContractDescription> i <xref:System.ServiceModel.Channels.BindingElement> obiektami, dlatego rozszerzenia importu zasad powinny być niezawodne dla tego zachowania.  
  
> [!IMPORTANT]
> Do importera mogą być przesyłane nieprawidłowe lub nieprawidłowe metadane. Upewnij się, że importerzy niestandardowi są niezawodne dla wszystkich form XML.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Importuj niestandardowe WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Instrukcje: Importuj potwierdzenia zasad niestandardowych](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Instrukcje: Napisz rozszerzenie dla ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
