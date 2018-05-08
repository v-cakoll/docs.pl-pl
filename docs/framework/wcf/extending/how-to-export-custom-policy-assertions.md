---
title: 'Instrukcje: Eksportowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 4182007d32ea857aa333542b4df29da18b8062df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-export-custom-policy-assertions"></a>Instrukcje: Eksportowanie niestandardowych asercji zasad
Potwierdzenia zasad opisano wymagania punktu końcowego usługi. Aplikacje usługi mogą używać niestandardowych asercji zasad w metadanych usługi do komunikowania się punkt końcowy, powiązanie lub kontrakt informacje o dostosowaniu do aplikacji klienckiej. Windows Communication Foundation (WCF) służy do potwierdzenia w wyrażeniach zasad dołączona w powiązania WSDL na punkt końcowy, operacji lub komunikat tematów, w zależności od możliwości lub wymagania, które komunikują się wyeksportować.  
  
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
 [Instrukcje: importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
