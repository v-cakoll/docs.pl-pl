---
title: "Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0"
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
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 214e0de13ba362bf4f101a665e943a424c56363c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Klienci są przewodowy poziom zgodny z 3.0 rozszerzenia usługi sieci Web dla usług platformy Microsoft .NET (WSE), kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów są skonfigurowane do korzystania z sierpnia 2004 wersja specyfikacji WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Aby skonfigurować klienta programu WCF na potrzeby współdziałania z usługą sieci Web programu WSE 3.0  
  
1.  Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta usługi sieci Web programu WSE 3.0.  
  
     Usługi sieci Web programu WSE [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utworzeniu klasy klienta.  
  
     Aby uzyskać więcej informacji o tworzeniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.  
  
     Następujące klasy jest częścią [współpracy z WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41) próbki.  
  
    1.  Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.  
  
         Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` która pochodzi z <xref:System.ServiceModel.Channels.Binding> klasy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Dodaj właściwości do klasy, która określa potwierdzenia gotowe WSE, czy wymagane są klucze pochodnej czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości.  
  
         Poniższy przykładowy kod definiuje `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` właściwości, które określają potwierdzenia gotowe WSE, czy wymagane są klucze pochodnej czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości, odpowiednio.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Zastąpienie <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody do ustawiania właściwości powiązania.  
  
         Poniższy przykład kodu określa transportu, kodowania wiadomości i ustawienia ochrony wiadomości przez pobieranie wartości z `SecurityAssertion` i `MessageProtectionOrder` właściwości.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  W kodzie aplikacji klienta Dodaj kod, aby ustawić właściwości powiązania.  
  
     Poniższy przykład kodu Określa, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta musi używać uwierzytelniania i ochrony wiadomości, zgodnie z definicją w WSE 3.0 `AnonymousForCertificate` potwierdzenia zabezpieczeń gotowe. Ponadto wymagane są bezpieczne sesje i kluczy pochodnych.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odpowiadają właściwości potwierdzenia zabezpieczeń gotowe WSE 3.0. Wiązanie niestandardowe o nazwie `WseHttpBinding`, jest następnie używany do określania właściwości powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 [Współdziałanie z WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
