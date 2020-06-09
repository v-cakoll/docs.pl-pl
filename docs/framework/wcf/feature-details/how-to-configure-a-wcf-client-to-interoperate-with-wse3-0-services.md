---
title: 'Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579582"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0
Klienci korzystający z programu Windows Communication Foundation (WCF) są zgodną z usługami sieci Web udoskonalenia 3,0 dla usług Microsoft .NET (WSE), gdy klienci WCF są skonfigurowani do korzystania z wersji z sierpnia 2004 specyfikacji WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Aby skonfigurować klienta WCF do współdziałania z usługą sieci Web WSE 3,0  
  
1. Uruchom narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , aby utworzyć klienta WCF dla usługi sieci Web WSE 3,0.  
  
     W przypadku usługi sieci Web WSE tworzona jest Klasa klienta WCF.  
  
     Aby uzyskać szczegółowe informacje o tworzeniu klienta WCF, zobacz [How to: Create a Client](../how-to-create-a-wcf-client.md).  
  
2. Utwórz klasę, która reprezentuje powiązanie, które może komunikować się z usługami sieci Web WSE 3,0.  
  
     Następująca Klasa jest częścią [współdziałania z](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) przykładem WSE.  
  
    1. Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.  
  
         Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` , która dziedziczy z <xref:System.ServiceModel.Channels.Binding> klasy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. Dodaj właściwości do klasy, która określa WSE gotowe, bez względu na to, czy klucze pochodne są wymagane, czy są używane bezpieczne sesje, czy potwierdzania podpisu są wymagane oraz ustawienia ochrony wiadomości.  
  
         Poniższy przykład kodu definiuje `SecurityAssertion` właściwości,, `RequireDerivedKeys` `EstablishSecurityContext` i `MessageProtectionOrder` . Określają one WSE gotowe, niezależnie od tego, czy klucze pochodne są wymagane, czy są używane bezpieczne sesje, czy potwierdzenia podpisu są wymagane i odpowiednio ustawienia ochrony wiadomości.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. Zastąp <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodę, aby ustawić właściwości powiązania.  
  
         Poniższy przykład kodu określa ustawienia transportu, kodowania komunikatów i ochrony wiadomości, pobierając wartości `SecurityAssertion` `MessageProtectionOrder` właściwości i.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. W kodzie aplikacji klienckiej Dodaj kod, aby ustawić właściwości powiązania.  
  
     Poniższy przykład kodu określa, że klient WCF musi używać ochrony komunikatów i uwierzytelniania zgodnie z opisem w `AnonymousForCertificate` potwierdzeniu zabezpieczeń WSE 3,0 gotowe. Dodatkowo wymagane są bezpieczne sesje i klucze pochodne.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje niestandardowe powiązanie, które uwidacznia właściwości odpowiadające właściwościom WSE 3,0 gotowe Security Assertion. Niestandardowe powiązanie o nazwie jest `WseHttpBinding` następnie używane do określania właściwości powiązań dla klienta WCF.  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.Binding>
- [Współdziałanie z WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
