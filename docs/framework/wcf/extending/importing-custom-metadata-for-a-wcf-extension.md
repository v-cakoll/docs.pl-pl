---
title: Importowanie niestandardowych metadanych dla rozszerzenia WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9208a73f6a35e4c05ab9be612491f3f7db792a5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Importowanie niestandardowych metadanych dla rozszerzenia WCF
W [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], importu metadanych jest proces generowania abstrakcyjną reprezentacją usługi lub jego składniki z jego metadanych. Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień, <xref:System.ServiceModel.Channels.Binding> wystąpień lub <xref:System.ServiceModel.Description.ContractDescription> wystąpień z WSDL dokumentu usługi. Aby zaimportować metadane usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], korzystać z implementacji <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> klasy abstrakcyjnej. Typy, które pochodzą z <xref:System.ServiceModel.Description.MetadataImporter> klasa implementuje pomocy technicznej dla importowania formaty metadanych, które korzystają z protokołu WS-Policy zaimportować logikę w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Niestandardowych metadanych składa się z elementów XML, których nie można zaimportować importerów metadanych dostarczane przez system. Zwykle obejmuje niestandardowe rozszerzenia WSDL oraz niestandardowych asercji zasad.  
  
 Ta sekcja opisuje sposób importowania niestandardowe rozszerzenia WSDL i potwierdzeń zasad. Nie skupić się na sam proces importowania. Aby uzyskać więcej informacji o sposobie używania typy, które eksportowanie i Importowanie metadanych niezależnie od tego, czy metadane niestandardowych lub obsługiwane przez system, zobacz [eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Omówienie  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typu to implementacja <xref:System.ServiceModel.Description.MetadataImporter> dołączone do klasy abstrakcyjnej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter> Typu importuje WSDL metadanych za pomocą dołączonego zasad, które są powiązane w <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> obiektu. Potwierdzenia zasad i rozszerzenia WSDL, które nie rozpoznają importerów domyślne są przekazywane do żadnych zarejestrowanych zasady niestandardowe i importerów WSDL do zaimportowania. Zazwyczaj importerów są wdrażane do obsługi elementy wiązania zdefiniowane przez użytkownika lub zmodyfikować importowanych kontraktu.  
  
 W tej sekcji opisano:  
  
1.  Jak wdrożyć i używać <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu, który udostępnia dane WSDL niestandardowych importerów przed Generowanie opisy i generowanie kodu. Ten interfejs umożliwia Sprawdź lub zmodyfikuj opis typów i wykonywane przy użyciu określonego zestawu metadanych kompilacji kodu.  
  
2.  Jak wdrożyć i używać <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu, który uwidacznia potwierdzeń zasad importerów przed generowania opis obiektów. Ten interfejs umożliwia Sprawdź lub zmodyfikuj powiązanie lub kontraktu na podstawie zasad pobrany.  
  
 Aby uzyskać więcej informacji na temat eksportowania niestandardowych WSDL i potwierdzeń zasad, zobacz [Eksportowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Importowanie rozszerzenia WSDL niestandardowych  
 Aby dodać obsługę importowanie rozszerzenia WSDL, zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs, a następnie dodaj do implementacji <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> właściwości. <xref:System.ServiceModel.Description.WsdlImporter> Można również ładować implementacje <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs zarejestrowany w pliku konfiguracyjnym aplikacji. Warto zauważyć, że liczba importerów WSDL są rejestrowane przez domyślną kolejność zarejestrowanych importerów WSDL jest znacząca.  
  
 Gdy załadowany i używane przez niestandardowe importerów WSDL <xref:System.ServiceModel.Description.WsdlImporter>, pierwszy <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> metoda jest wywoływana, aby umożliwić modyfikowanie metadanych przed proces importowania. Następnie umów są importowane po upływie którego <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> metoda jest wywoływana, aby umożliwić modyfikowanie kontrakty zaimportowane z metadanych. Na koniec <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> metoda jest wywoływana, aby umożliwić modyfikowanie importowanych punktów końcowych.  
  
 Aby uzyskać więcej informacji, zobacz [porady: importowanie niestandardowych WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Importowanie niestandardowych asercji zasad  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu i [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) automatycznie obsługi przetwarzania różnych typów potwierdzenia zasad w wyrażeniach zasady dołączone do dokumentów WSDL. Te narzędzia zbierania, normalizacji i scalić dołączony do powiązania WSDL i porty WSDL wyrażenie zasad.  
  
 Aby dodać obsługę importowanie niestandardowych asercji zasad, zaimplementuj <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejs, a następnie dodaj do implementacji <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> właściwości. <xref:System.ServiceModel.Description.MetadataImporter> Można również ładować implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejs zarejestrowany w pliku konfiguracyjnym aplikacji. Warto zauważyć, że liczba importerów zasad są rejestrowane przez domyślną kolejność importerów zasad zarejestrowanych jest znacząca.  
  
 System metadanych wielokrotnie wywołuje <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metody na wszystkich zarejestrowanych zasad zaimportuj rozszerzeń dla każdej kombinacji zasad alternatywnych dołączony do tematów zasad komunikatu, operacja i punktu końcowego. Podczas importowania portu WSDL, zasady dołączonych do portu i odpowiednie Powiązanie WSDL są scalane przed wywołaniem do rozszerzenia importu zasad. Zasad alternatywnych są udostępniane za pomocą <xref:System.ServiceModel.Description.PolicyConversionContext> jako <xref:System.ServiceModel.Description.PolicyAssertionCollection> obiektów. Każdy <xref:System.ServiceModel.Description.PolicyAssertionCollection> jest kolekcją potwierdzeń zasad reprezentowany przez <xref:System.Xml.XmlElement> obiektów.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> i <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> właściwości <xref:System.ServiceModel.Description.PolicyConversionContext> obiekt Uwidacznianie <xref:System.ServiceModel.Description.ContractDescription> i <xref:System.ServiceModel.Channels.BindingElement> obiektów, które zostały zaimportowane z pliku WSDL. Rozszerzenia importu zasad przetworzyć potwierdzeń zasad przez wyszukiwanie wystąpienia typu potwierdzenia konkretne zasady, zmiany odpowiednie do <xref:System.ServiceModel.Description.ContractDescription> lub <xref:System.ServiceModel.Channels.BindingElement> obiektów, a następnie usuwając potwierdzeń zasad z odpowiedniego <xref:System.ServiceModel.Description.PolicyAssertionCollection> wystąpienia.  
  
 `wsp:Optional` Atrybut i wyrażenia zagnieżdżonych zasad są nie znormalizowany, więc rozszerzenia importu zasad musi obsługiwać tych elementów składowych zasad. Ponadto rozszerzenia importu zasad może zostać wywołana wiele razy z tym samym <xref:System.ServiceModel.Description.ContractDescription> i <xref:System.ServiceModel.Channels.BindingElement> obiekty, dlatego rozszerzenia importu zasad powinien być odporny to zachowanie.  
  
> [!IMPORTANT]
>  Nieprawidłowy lub niewłaściwego metadane mogą być przekazywane do importera. Upewnij się, że importerów niestandardowe są niezawodne do wszystkich formularzy XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: importowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)  
 [Instrukcje: importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)  
 [Instrukcje: pisanie rozszerzenia dla elementu ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
