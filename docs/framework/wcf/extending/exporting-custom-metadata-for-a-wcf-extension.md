---
title: Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 5134b57c59268b139239021bc2b4f6f4538ad27d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857964"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF
W Windows Communication Foundation (WCF), eksportowanie metadanych jest proces opisujące punkty końcowe usługi i wyświetlaniu je do reprezentacji równoległych, standardowe, której klienci mogą używać, aby zrozumieć sposób korzystania z usługi. Niestandardowych metadanych zawiera elementy XML, które nie można wyeksportować eksportera metadanych dostarczane przez system. Zazwyczaj zawiera elementy niestandardowe WSDL dla zachowania zdefiniowanych przez użytkownika i elementy powiązań asercji zasad dotyczących możliwości i wymagania dotyczące powiązania i kontrakty.  
  
 W tej sekcji opisano eksportowanie niestandardowych plików WSDL lub asercji zasad i koncentruje się na sam proces eksportowania. Aby uzyskać więcej informacji o sposobie używania typów, które eksportowanie i Importowanie metadanych, niezależnie od tego, czy metadane są niestandardowe lub skonstruowany systemu, zobacz [eksportowania i importowania metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Omówienie  
 Gdy publikowane są metadane, za pomocą <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> jest badany i XSD i — w tym asercji zasad — WSDL, które są generowane dla wszystkich umów i powiązań, które może obsługiwać usługi WCF, za pomocą atrybutów dostarczane przez system i powiązania. Jednakże atrybuty niestandardowe zachowanie lub elementy powiązania wymagają obsługi przed prawidłowo wyeksportowany.  
  
 W tej sekcji opisano:  
  
1. Jak implementować oraz używać <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interfejs, który udostępnia dane nowej generacji WSDL do Ciebie, przed opublikowaniem WSDL.  
  
2. Jak implementować oraz używać <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs, który udostępnia dane zasad dla użytkownika przed wyeksportowaniem asercji zasad danych WSDL.  
  
 Aby uzyskać więcej informacji na temat importowanie niestandardowych plików WSDL i asercji zasad zobacz [importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Eksportowanie elementów niestandardowych plików WSDL  
 Implementowanie <xref:System.ServiceModel.Description.IWsdlExportExtension> na zachowanie działania, zachowanie kontraktu, zachowanie punktu końcowego lub element powiązania (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, lub <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> odpowiednio) i Wstaw zachowania lub elementy powiązania do Opis usługi, którą chcesz wyeksportować. (Aby uzyskać więcej informacji na temat zachowania wstawiania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Jest wywoływana dla każdego punktu końcowego i każdy punkt końcowy eksportuje kontrakt najpierw Jeśli nie zostały jeszcze wyeksportowane. W obu procesu eksportu mogą uczestniczyć w zależności od potrzeb:  
  
- Użyj <xref:System.ServiceModel.Description.WsdlContractConversionContext> do modyfikowania wyeksportowanego metadanych w <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
- Użyj <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> do modyfikowania wyeksportowanego metadanych dla punktu końcowego w <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody.  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> Metoda jest wywoływana we wszystkich <xref:System.ServiceModel.Description.IWsdlExportExtension> implementacji w <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> wystąpienie, które jest eksportowany.  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Metoda jest wywoływana we wszystkich <xref:System.ServiceModel.Description.IWsdlExportExtension> implementacji przy użyciu <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wystąpienie, które jest eksportowany.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Eksportowanie niestandardowych WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) i próbki [niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Eksportowanie niestandardowych asercji zasad  
 Implementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension> na <xref:System.ServiceModel.Channels.BindingElement> i Dodaj element powiązania do powiązania do pisania niestandardowych asercji zasad o powiązaniu pomoc techniczna i Umowa możliwości WSDL. <xref:System.ServiceModel.Description.IPolicyExportExtension> Jest wywoływana jeden raz podczas eksportowania elementu powiązania zaimplementowanego w powiązaniu i przekazuje <xref:System.ServiceModel.Description.PolicyConversionContext> do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody. Można użyć metod na <xref:System.ServiceModel.Description.PolicyConversionContext> wystąpienie do dodania do asercji zasad dołączone do Powiązanie WSDL na tematy wiadomości, operacja lub punktu końcowego.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Eksportowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Eksportowanie niestandardowych plików WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Instrukcje: Eksportowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)
- [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
