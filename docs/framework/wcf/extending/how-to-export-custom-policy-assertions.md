---
title: 'Instrukcje: eksportowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795670"
---
# <a name="how-to-export-custom-policy-assertions"></a>Instrukcje: eksportowanie niestandardowych asercji zasad
Potwierdzenia zasad opisują możliwości i wymagania punktu końcowego usługi. Aplikacje usług mogą używać niestandardowych potwierdzeń zasad w metadanych usługi do przekazywania informacji o dostosowywaniu punktów końcowych, powiązań lub umów do aplikacji klienckiej. Za pomocą Windows Communication Foundation (WCF) można eksportować potwierdzenia w wyrażeniach zasad dołączonych do powiązań WSDL w podmiotach punktu końcowego, operacji lub komunikatu, w zależności od możliwości lub wymagań, które komunikujesz.  
  
 Potwierdzenia zasad niestandardowych są eksportowane przez zaimplementowanie <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> na i wstawianie elementu powiązania bezpośrednio do powiązania punktu końcowego usługi lub przez zarejestrowanie elementu powiązania w aplikacji. plik konfiguracji. Implementacja eksportu zasad powinna dodać <xref:System.Xml.XmlElement?displayProperty=nameWithType> potwierdzenie zasad niestandardowych jako wystąpienie do odpowiedniej <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody w <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> przekazaniu na metodę.  
  
 Ponadto należy sprawdzić <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Właściwość <xref:System.ServiceModel.Description.WsdlExporter> klasy i wyeksportować zagnieżdżone wyrażenia zasad i atrybuty struktury zasad w prawidłowej przestrzeni nazw na podstawie określonej wersji zasad.  
  
 Aby zaimportować potwierdzenia zasad niestandardowych, zobacz <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> i [instrukcje: Importuj potwierdzenia](how-to-import-custom-policy-assertions.md)zasad niestandardowych.  
  
### <a name="to-export-custom-policy-assertions"></a>Aby wyeksportować potwierdzenia zasad niestandardowych  
  
1. Zaimplementuj <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>interfejs na. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> Poniższy przykład kodu pokazuje implementację niestandardowej potwierdzeń zasad na poziomie powiązania.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Wstaw element Binding do powiązania punktu końcowego albo programowo lub za pomocą pliku konfiguracji aplikacji. Zapoznaj się z poniższymi procedurami.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Aby wstawić element powiązania przy użyciu pliku konfiguracji aplikacji  
  
1. Zaimplementuj <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> dla elementu niestandardowego powiązania potwierdzenia zasad.  
  
2. Dodaj rozszerzenie elementu Binding do pliku konfiguracji przy użyciu [ \<elementu > BindingElementExtensions](../../configure-apps/file-schema/wcf/bindingelementextensions.md) .  
  
3. Utwórz niestandardowe powiązanie przy użyciu <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Aby programowo wstawić element powiązania  
  
1. Utwórz nowy <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> i dodaj go <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>do.  
  
2. Dodaj niestandardowe powiązanie z kroku 1. do nowego punktu końcowego i Dodaj nowy punkt końcowy usługi do elementu <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> , <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> wywołując metodę.  
  
3. Otwórz okno <xref:System.ServiceModel.ServiceHost>. Poniższy przykład kodu pokazuje Tworzenie niestandardowego powiązania i programistyczne Wstawianie elementów powiązania.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Instrukcje: Importuj potwierdzenia zasad niestandardowych](how-to-import-custom-policy-assertions.md)
