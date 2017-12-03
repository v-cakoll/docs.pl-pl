---
title: 'Instrukcje: Eksportowanie niestandardowych asercji zasad'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1cfce32a7e7099a601c76874c8ca951488335fc6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-export-custom-policy-assertions"></a>Instrukcje: Eksportowanie niestandardowych asercji zasad
Potwierdzenia zasad opisano wymagania punktu końcowego usługi. Aplikacje usługi mogą używać niestandardowych asercji zasad w metadanych usługi do komunikowania się punkt końcowy, powiązanie lub kontrakt informacje o dostosowaniu do aplikacji klienckiej. Można użyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] można wyeksportować potwierdzenia w wyrażeniach zasad dołączona w powiązania WSDL na punkt końcowy, operacji lub komunikat tematów, w zależności od możliwości lub wymagania komunikują się.  
  
 Niestandardowych asercji zasad są eksportowane z zastosowaniem <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs w <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i wstawianie element powiązania bezpośrednio do powiązania punktu końcowego usługi lub poprzez zarejestrowanie element powiązania w aplikacji plik konfiguracji. Implementacji eksportu zasad należy dodać potwierdzenia Twojej zasad niestandardowych jako <xref:System.Xml.XmlElement?displayProperty=nameWithType> wystąpienie do odpowiedniego <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> przekazany <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody.  
  
 Ponadto należy sprawdzić <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwość <xref:System.ServiceModel.Description.WsdlExporter> klasy i eksportowanie zasad zagnieżdżonych wyrażeń atrybutów framework zasad w poprawną przestrzeń nazw na podstawie określonej wersji zasad.  
  
 Aby zaimportować niestandardowych asercji zasad, zobacz <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> i [porady: importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Aby wyeksportować niestandardowych asercji zasad  
  
1.  Implementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs w <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Poniższy przykładowy kod przedstawia implementację potwierdzenia zasad niestandardowych, na poziomie powiązania.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Wstaw element powiązania do punktu końcowego powiązanie albo programowo lub przy użyciu pliku konfiguracji aplikacji. Zobacz poniższe procedury.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Aby wstawić element powiązania przy użyciu pliku konfiguracji aplikacji  
  
1.  Implementowanie <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> Twojego elementu powiązania potwierdzenia zasad niestandardowych.  
  
2.  Dodaj element rozszerzenia powiązania do pliku konfiguracji przy użyciu [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) elementu.  
  
3.  Tworzenie niestandardowego powiązania za pomocą <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Aby wstawić element powiązania programowo  
  
1.  Utwórz nową <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i dodaj go do <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Dodawanie niestandardowego powiązania z kroku 1. do nowego punktu końcowego i Dodaj ten nowy punkt końcowy usługi do <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
3.  Otwórz <xref:System.ServiceModel.ServiceHost>. Poniższy przykładowy kod przedstawia tworzenie niestandardowego powiązania i programowe wstawiania elementów wiązania.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [Porady: importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
