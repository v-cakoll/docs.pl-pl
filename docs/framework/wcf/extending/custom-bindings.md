---
title: Powiązania niestandardowe
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 694b4faaafea62799a96aabe8f023a0d495f8d50
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866771"
---
# <a name="custom-bindings"></a>Powiązania niestandardowe
Możesz użyć <xref:System.ServiceModel.Channels.CustomBinding> klasy, gdy jedno z powiązań dostarczanych przez system nie spełnia wymagania dotyczące usługi. Wszystkie powiązania są konstruowane na podstawie uporządkowany zestaw elementów wiązania. Powiązania niestandardowe mogą być zbudowane z zestaw elementów powiązania dostarczane przez system lub może zawierać elementów zdefiniowanych przez użytkownika niestandardowego powiązania. Elementy powiązania niestandardowego, na przykład umożliwia korzystanie z nowego transportu lub koderów na punkt końcowy usługi. Przykłady pracy, zobacz [niestandardowe powiązanie przykłady](https://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08). Aby uzyskać więcej informacji, zobacz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Konstrukcja powiązania niestandardowego  
 Powiązanie niestandardowe jest tworzony przy użyciu <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktora z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:  
  
-   U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> klasę, która umożliwia przepływu transakcji.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> klasę, która zapewnia sesji i kolejność mechanizmów, zgodnie z definicją w specyfikacji WS-ReliableMessaging. Sesja może krzyżowe pośredników SOAP i mechanizm transportu.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.SecurityBindingElement> klasę, która zapewnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufnością.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> klasę, która zapewnia możliwość mieć dwa sposób paradygmacie komunikacji przy użyciu protokołu transportu, która nie obsługuje komunikację dupleksową natywnie, takich jak HTTP.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.OneWayBindingElement>) klasę, która zapewnia komunikację jednokierunkową.  
  
-   Następnym ekranem jest opcjonalny strumienia elementu powiązania zabezpieczeń, który może być jednym z następujących czynności.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Następnym ekranem jest element powiązania z kodowania komunikatu wymagane. Można użyć koder komunikatu lub jeden z trzech powiązania kodowania komunikatu:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 W dolnej części jest element wymagany transportu. Można użyć własnych transportu lub jedną z następujących elementy powiązania transportu, przez Windows Communication Foundation (WCF):  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 Poniższa tabela podsumowuje opcje dla każdej warstwy.  
  
|Warstwa|Opcje|Wymagane|  
|-----------|-------------|--------------|  
|Transakcje|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Nie|  
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Nie|  
|Zabezpieczenia|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Nie|  
|Kodowanie|Tekst, niestandardowe dane binarne, komunikat transmisji optymalizacji mechanizm (MTOM)|Tak|  
|Transportu|TCP, HTTP i HTTPS, nazwanych potoków (znany także jako IPC) między równorzędnych (P2P), Usługa kolejkowania komunikatów (MSMQ), niestandardowe|Tak|  
  
 Ponadto można zdefiniować własne elementy powiązania i wstawione między dowolnymi poprzedniej warstwy zdefiniowanej przez użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Instrukcje: dostosowywanie powiązania udostępnionego przez system](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Powiązanie niestandardowe](../../../../docs/framework/wcf/samples/custom-binding.md)
