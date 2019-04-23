---
title: Importowanie niestandardowych metadanych dla rozszerzenia WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 830829be98202c97a9fc2b34e31da25967292efb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339973"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Importowanie niestandardowych metadanych dla rozszerzenia WCF
W Windows Communication Foundation (WCF), importowanie metadanych jest proces generowania abstrakcyjną reprezentację usługi lub jej części składowe z jego metadanych. Na przykład, można zaimportować WCF <xref:System.ServiceModel.Description.ServiceEndpoint> przypadkach <xref:System.ServiceModel.Channels.Binding> wystąpień lub <xref:System.ServiceModel.Description.ContractDescription> wystąpień na podstawie pliku WSDL dokumentów dla usługi. Aby zaimportować metadane usługi w programie WCF, należy korzystać z implementacji <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasy abstrakcyjnej. Typy, które wynikają z <xref:System.ServiceModel.Description.MetadataImporter> klasa implementuje pomocy technicznej w przypadku importowania formaty metadanych, które korzystają z protokołu WS-Policy zaimportować logiki w programie WCF.  
  
 Niestandardowych metadanych zawiera elementy XML, które importerów metadanych dostarczane przez system nie może zaimportować. Zazwyczaj zawiera niestandardowe rozszerzenia WSDL i niestandardowych asercji zasad.  
  
 W tej sekcji opisano, jak importować niestandardowe rozszerzenia WSDL i asercji zasad. Nie koncentruje się na sam proces importowania. Aby uzyskać więcej informacji o sposobie używania typów, które eksportowanie i Importowanie metadanych, niezależnie od tego, czy metadane są niestandardowe lub obsługiwane przez system, zobacz [eksportowania i importowania metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Omówienie  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu jest implementacją <xref:System.ServiceModel.Description.MetadataImporter> abstrakcyjna klasa dołączone do programu WCF. <xref:System.ServiceModel.Description.WsdlImporter> Typu importuje metadane WSDL z dołączonym zasadami, które są powiązane w <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> obiektu. Asercji zasad i rozszerzenia WSDL, które nie rozpoznają importerów domyślne są przekazywane do dowolnego zarejestrowanego zasady niestandardowe i importerów WSDL importowania. Zazwyczaj importers są implementowane w celu zapewnienia obsługi elementy powiązań zdefiniowanych przez użytkownika lub modyfikowanie importowanych kontraktu.  
  
 W tej sekcji opisano:  
  
1. Jak implementować oraz używać <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejs, który udostępnia dane WSDL niestandardowe importerów przed Generowanie opisy i generowanie kodu. Aby sprawdzić lub zmodyfikuj opis typów i kompilacja kodu, wykonywane przy użyciu określonego zestawu metadanych, można użyć tego interfejsu.  
  
2. Jak implementować oraz używać <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs, który udostępnia asercji zasad importerów przed generacji obiektów opis. Aby przejrzeć lub zmodyfikować binding lub umowy na podstawie pobranego zasad, można użyć tego interfejsu.  
  
 Aby uzyskać więcej informacji na temat eksportowania niestandardowych plików WSDL i asercji zasad, zobacz [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Importowanie niestandardowych plików WSDL rozszerzeń  
 Aby dodać obsługę importowania rozszerzenia WSDL, należy zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejsu, a następnie dodaj do implementacji <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> właściwości. <xref:System.ServiceModel.Description.WsdlImporter> Można również załadować implementacje <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs zarejestrowany w pliku konfiguracyjnym aplikacji. Pamiętaj, że liczba importerów WSDL są rejestrowane przez domyślną kolejność zarejestrowanych importerów WSDL jest znacząca.  
  
 Kiedy niestandardowe importerów WSDL jest ładowany i używane przez <xref:System.ServiceModel.Description.WsdlImporter>najpierw <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> metoda jest wywoływana, aby umożliwić modyfikowanie metadanych przed proces importowania. Następnie kontrakty te są importowane po upływie którego <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> metoda jest wywoływana, aby umożliwić modyfikowanie kontraktów zaimportowane z metadanych. Na koniec <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> metoda jest wywoływana, aby umożliwić modyfikowanie zaimportowanych punktów końcowych.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Importowanie niestandardowych plików WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Importowanie niestandardowych asercji zasad  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu i [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) automatycznie obsługiwać przetwarzanie różnych typów asercji zasad w wyrażeniach zasady dołączone do dokumenty WSDL. Te narzędzia zbierać, normalizacji operacji WE / i scalić wyrażenia zasad dołączone do powiązania WSDL i porty WSDL.  
  
 Aby dodać obsługę importowanie niestandardowych asercji zasad, należy zaimplementować <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu, a następnie dodaj do implementacji <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> właściwości. <xref:System.ServiceModel.Description.MetadataImporter> Można również załadować implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejs zarejestrowany w pliku konfiguracyjnym aplikacji. Pamiętaj, że liczba importerów zasad są rejestrowane przez domyślną kolejność importerów zasad zarejestrowanych ma znaczenie.  
  
 System metadanych wielokrotnie wywołuje <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metody na wszystkich zarejestrowanych zasad zaimportowanie rozszerzeń dla każdej kombinacji zasad alternatywnych dołączone do przedmioty zasad wiadomości, operacja i punktu końcowego. Podczas importowania portu WSDL, zasady dołączonych do portu i odpowiednie Powiązanie WSDL są scalane przed wywołaniem do rozszerzenia importu zasad. Zasad alternatywnych są udostępniane za pośrednictwem <xref:System.ServiceModel.Description.PolicyConversionContext> jako <xref:System.ServiceModel.Description.PolicyAssertionCollection> obiektów. Każdy <xref:System.ServiceModel.Description.PolicyAssertionCollection> to zbiór asercji zasad reprezentowany przez <xref:System.Xml.XmlElement> obiektów.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> i <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> właściwości <xref:System.ServiceModel.Description.PolicyConversionContext> obiektu udostępniają <xref:System.ServiceModel.Description.ContractDescription> i <xref:System.ServiceModel.Channels.BindingElement> obiekty, które zostały zaimportowane z pliku WSDL. Rozszerzenia importu zasad przetwarzania asercji zasad, wyszukując wystąpień typu potwierdzenie konkretne zasady, dzięki czemu odpowiednie zmiany do <xref:System.ServiceModel.Description.ContractDescription> lub <xref:System.ServiceModel.Channels.BindingElement> obiekty i usunąć z odpowiedniego asercjizasad<xref:System.ServiceModel.Description.PolicyAssertionCollection> wystąpienia.  
  
 `wsp:Optional` Atrybut i wyrażenia zasad zagnieżdżone są nie znormalizować, więc rozszerzenia importu zasad musi obsługiwać te konstrukcje zasad. Ponadto rozszerzenia importu zasad może wywoływać wielokrotnie z takimi samymi <xref:System.ServiceModel.Description.ContractDescription> i <xref:System.ServiceModel.Channels.BindingElement> obiekty, dlatego rozszerzenia importu zasad powinny być niezawodne do zachowania.  
  
> [!IMPORTANT]
>  Nieprawidłowe lub niepoprawne metadane mogą być przekazywane do importera. Upewnij się, że niestandardowe importerów niezawodne do wszystkich form XML.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Import Custom WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Instrukcje: Importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
