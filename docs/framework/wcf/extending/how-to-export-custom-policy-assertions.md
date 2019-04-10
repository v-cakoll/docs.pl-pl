---
title: 'Instrukcje: eksportowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 4e3835b0d699d58eb55e06ed3ade1328ec30b2ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213631"
---
# <a name="how-to-export-custom-policy-assertions"></a>Instrukcje: eksportowanie niestandardowych asercji zasad
Asercji zasad opisano możliwości i wymagania dotyczące punktu końcowego usługi. Aplikacje usługi można użyć niestandardowych asercji zasad w metadanych usługi do komunikacji z punktu końcowego, binding lub umowy informacje o dostosowaniu do aplikacji klienckiej. Windows Communication Foundation (WCF) umożliwia eksportowanie asercji w wyrażeniach zasad dołączone w powiązaniach WSDL na punkt końcowy, operacji lub tematów wiadomości, w zależności od możliwości i wymagania, które komunikują się.  
  
 Niestandardowych asercji zasad są eksportowane przez zaimplementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu na <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i wstawianie elementu powiązania bezpośrednio do powiązania punktu końcowego usługi lub rejestrując element powiązania w aplikacji plik konfiguracji. Implementacji eksportu zasad należy dodać swoje potwierdzeń niestandardowych zasad jako <xref:System.Xml.XmlElement?displayProperty=nameWithType> wystąpienia do odpowiednich <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> przekazany do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody.  
  
 Ponadto należy sprawdzić <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwość <xref:System.ServiceModel.Description.WsdlExporter> klasy i eksportowanie zasad zagnieżdżonych wyrażeń zasad framework atrybutów w poprawną przestrzeń nazw określona wersja zasad w oparciu.  
  
 Aby importowanie niestandardowych asercji zasad, zobacz <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> i [jak: Importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Aby Eksportowanie niestandardowych asercji zasad  
  
1.  Implementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu na <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Poniższy przykład kodu pokazuje implementację asercję zasad niestandardowych na poziomie powiązania.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Wstaw element powiązania do endpoint powiązanie albo programowo lub za pomocą pliku konfiguracji aplikacji. Zobacz poniższe procedury.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Aby wstawić element powiązania przy użyciu pliku konfiguracji aplikacji  
  
1.  Implementowanie <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> odniesieniu do danego elementu powiązania asercji zasad niestandardowych.  
  
2.  Dodaj rozszerzenie elementu powiązania do plików konfiguracji przy użyciu [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) elementu.  
  
3.  Tworzenie niestandardowego powiązania za pomocą <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Aby programowo wstawić element powiązania  
  
1.  Utwórz nową <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i dodać go do <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Dodawanie niestandardowego powiązania z kroku 1. do nowego punktu końcowego i dodać ten nowy punkt końcowy usługi <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
3.  Otwórz <xref:System.ServiceModel.ServiceHost>. W poniższym przykładzie kodu pokazano tworzenie powiązania niestandardowego i programowe wstawianie elementów wiązania.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Instrukcje: importowanie niestandardowych asercji zasad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
