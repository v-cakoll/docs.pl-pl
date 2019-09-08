---
title: Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797194"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF
W programie Windows Communication Foundation (WCF) Eksport metadanych to proces opisywania punktów końcowych usługi i projekcji ich w równoległej, ustandaryzowanej reprezentacji, z której klienci mogą zrozumieć, jak korzystać z usługi. Metadane niestandardowe składają się z elementów XML, których nie można eksportować przez eksporterów metadanych dostarczonych przez system. Zazwyczaj obejmuje to niestandardowe elementy WSDL dla zachowań zdefiniowanych przez użytkownika i elementów powiązania oraz potwierdzeń zasad o możliwościach i wymaganiach dotyczących powiązań i umów.  
  
 W tej sekcji opisano eksportowanie niestandardowych zatwierdzeń WSDL lub zasad i nie koncentruje się na samym procesie eksportowania. Aby uzyskać więcej informacji na temat korzystania z typów eksportujących i importowanych metadanych niezależnie od tego, czy metadane są niestandardowe, czy skonstruowane przez system, zobacz [Eksportowanie i Importowanie metadanych](../feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Omówienie  
 Gdy metadane są publikowane przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> , są badane i XSD oraz WSDL — łącznie z potwierdzeniami zasad — są generowane dla wszystkich kontraktów i powiązań, które mogą być obsługiwane przez funkcję WCF przy użyciu atrybutów i powiązań dostarczonych przez system. Jednak atrybuty zachowań niestandardowych lub elementy powiązania wymagają obsługi, zanim będą mogły zostać prawidłowo wyeksportowane.  
  
 W tej sekcji opisano:  
  
1. Jak zaimplementować i korzystać z <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interfejsu, który udostępnia dane generacji WSDL przed opublikowaniem WSDL.  
  
2. Jak zaimplementować i korzystać z <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu, który udostępnia dane zasad przed wyeksportowaniem potwierdzeń zasad w danych WSDL.  
  
 Aby uzyskać więcej informacji na temat importowania niestandardowych zatwierdzeń WSDL i zasad, zobacz [Importowanie niestandardowych metadanych dla rozszerzenia WCF](importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Eksportowanie niestandardowych elementów WSDL  
 <xref:System.ServiceModel.Description.IEndpointBehavior><xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Description.IContractBehavior>Zaimplementuj zachowanie <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> w ramach operacji, zachowanie kontraktu, zachowanie punktu końcowego lub element powiązania (,,, lub odpowiednio) i Wstaw zachowania lub elementy powiązania do <xref:System.ServiceModel.Description.IWsdlExportExtension> Opis usługi, którą próbujesz wyeksportować. (Aby uzyskać więcej informacji na temat wstawiania zachowań, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Jest wywoływana dla każdego punktu końcowego, a każdy punkt końcowy eksportuje kontrakt jako pierwszy, jeśli nie został jeszcze wyeksportowany. W zależności od potrzeb można wziąć udział w procesie eksportu:  
  
- Użyj, <xref:System.ServiceModel.Description.WsdlContractConversionContext> aby zmodyfikować wyeksportowane metadane <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> w metodzie.  
  
- Użyj, <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> aby zmodyfikować eksportowane metadane dla punktu końcowego <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> w metodzie.  
  
 Metoda jest wywoływana dla wszystkich <xref:System.ServiceModel.Description.IWsdlExportExtension> implementacji w <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> wyeksportowanym wystąpieniu. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>  Metoda jest wywoływana dla wszystkich <xref:System.ServiceModel.Description.IWsdlExportExtension> implementacji z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wyeksportowanym wystąpieniem. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>  
  
 Aby uzyskać więcej informacji, zobacz [jak: Eksportowanie niestandardowego WSDL](how-to-export-custom-wsdl.md) i przykładowej [niestandardowej publikacji WSDL](../samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Eksportowanie zatwierdzeń zasad niestandardowych  
 Zaimplementuj obiekt <xref:System.ServiceModel.Channels.BindingElement> naaiDodajelementBindingdopowiązania,abyzapisaćniestandardowepotwierdzeniazasaddotycząceobsługipowiązańimożliwościkontraktuwjęzykuWSDL.<xref:System.ServiceModel.Description.IPolicyExportExtension> Jest wywoływana raz podczas eksportowania zaimplementowanego elementu Binding w powiązaniu i <xref:System.ServiceModel.Description.PolicyConversionContext> przekazuje do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody. <xref:System.ServiceModel.Description.IPolicyExportExtension> Można użyć metod w <xref:System.ServiceModel.Description.PolicyConversionContext> wystąpieniu, aby dodać do potwierdzeń zasad dołączonych do powiązania WSDL w tematach komunikatów, operacji lub punktów końcowych.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Eksportuj potwierdzenia](how-to-export-custom-policy-assertions.md)zasad niestandardowych.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Eksportuj niestandardowy element WSDL](how-to-export-custom-wsdl.md)
- [Instrukcje: Eksportowanie zatwierdzeń zasad niestandardowych](how-to-export-custom-policy-assertions.md)
- [Importowanie niestandardowych metadanych dla rozszerzenia WCF](importing-custom-metadata-for-a-wcf-extension.md)
