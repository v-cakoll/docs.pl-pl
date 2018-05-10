---
title: Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: c2ae547f10e96a1fdc16fc428e98145fc81c59d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF
W konsoli Windows Communication Foundation (WCF) eksportowania metadanych jest proces opisujące punktów końcowych usługi i projekcji ich reprezentację równoległe, standardowe, której klienci mogą używać, aby zrozumieć sposób korzystania z usługi. Niestandardowych metadanych składa się z elementów XML nie można wyeksportować eksportera metadanych dostarczane przez system. Zazwyczaj zawiera elementy WSDL niestandardowe zachowania użytkownika i elementy powiązania i potwierdzeń zasad o możliwości i wymagania dotyczące powiązania i kontrakty.  
  
 W tej sekcji opisano eksportowanie niestandardowych WSDL lub potwierdzeń zasad, a nie skupić się na samym procesie eksportowanie. Aby uzyskać więcej informacji o sposobie używania typy, które eksportowanie i Importowanie metadanych niezależnie od tego, czy metadane są niestandardowe lub utworzone przez system, zobacz [eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Omówienie  
 Gdy publikowane są metadane, za pomocą <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> się zbadana i XSD i — w tym potwierdzeń zasad--WSDL generowane są wszystkie kontrakty i powiązania obsługującymi WCF za pomocą atrybutów dostarczane przez system i powiązania. Jednak powiązania elementów lub atrybutów niestandardowych zachowania wymagają obsługi przed poprawnie eksportowane.  
  
 W tej sekcji opisano:  
  
1.  Jak wdrożyć i używać <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interfejsu, który udostępnia WSDL generowania danych można przed opublikowaniem WSDL.  
  
2.  Jak wdrożyć i używać <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu, który udostępnia dane zasad dla użytkownika przed wyeksportowaniem potwierdzenia zasad w danych WSDL.  
  
 Aby uzyskać więcej informacji o importowaniu niestandardowych WSDL i potwierdzeń zasad, zobacz [importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Eksportowanie niestandardowych WSDL elementów  
 Implementowanie <xref:System.ServiceModel.Description.IWsdlExportExtension> na zachowanie operacji, zachowanie kontraktu, zachowania punktu końcowego lub element powiązania (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, lub <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> odpowiednio) i Wstaw zachowania lub powiązania elementów do Opis usługi, którą chcesz wyeksportować. (Aby uzyskać więcej informacji na temat wstawiania zachowania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Jest wywoływana dla każdego punktu końcowego, a każdy punkt końcowy eksportuje kontrakt najpierw Jeśli nie ma już wyeksportowane. W obu procesu eksportu mogą uczestniczyć w zależności od potrzeb:  
  
-   Użyj <xref:System.ServiceModel.Description.WsdlContractConversionContext> do modyfikowania wyeksportowanego metadanych w <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
-   Użyj <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> do modyfikowania wyeksportowanego metadanych dla punktu końcowego w <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody.  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> Metoda jest wywoływana we wszystkich <xref:System.ServiceModel.Description.IWsdlExportExtension> implementacji w <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> wystąpienie, które jest eksportowany.  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Metoda jest wywoływana we wszystkich <xref:System.ServiceModel.Description.IWsdlExportExtension> implementacje z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wystąpienie, które jest eksportowany.  
  
 Aby uzyskać więcej informacji, zobacz [porady: eksportu WSDL niestandardowe](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) i próbka [niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Eksportowanie niestandardowych asercji zasad  
 Implementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension> na <xref:System.ServiceModel.Channels.BindingElement> i Dodaj element powiązania do powiązania zapisu niestandardowych asercji zasad o powiązanie możliwości pomocy technicznej i kontraktu w języku WSDL. <xref:System.ServiceModel.Description.IPolicyExportExtension> Jest wywoływana raz podczas eksportowania elementu powiązania zaimplementowanego w powiązaniu i przekazuje <xref:System.ServiceModel.Description.PolicyConversionContext> do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody. Można użyć metod na <xref:System.ServiceModel.Description.PolicyConversionContext> wystąpienie do dodania do potwierdzenia zasad dołączony do powiązania WSDL na tematy wiadomości, operacji lub punktu końcowego.  
  
 Aby uzyskać więcej informacji, zobacz [porady: eksportowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: eksportowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Instrukcje: eksportowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)  
 [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
