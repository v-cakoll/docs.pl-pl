---
title: 'Instrukcje: Dostęp do usługi WSE 3.0 za pomocą klienta programu WCF'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 382762917e790d54dca31158f2b7ffde560c1427
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Instrukcje: Dostęp do usługi WSE 3.0 za pomocą klienta programu WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Klienci są przewodowy poziom zgodny z sieci Web usług ulepszenia (WSE) 3.0 dla usług Microsoft .NET, gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów są skonfigurowane do korzystania z sierpnia 2004 wersja specyfikacji WS-Addressing. Jednak usługi WSE 3.0 nie obsługują protokół exchange (MEX) metadanych, dlatego jeśli używasz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta, ustawienia zabezpieczeń nie są stosowane do wygenerowany [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta. W związku z tym należy określić ustawienia zabezpieczeń, które wymaga usługi WSE 3.0 po [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest generowany przez klienta.  
  
 Można zastosować te ustawienia zabezpieczeń przy użyciu niestandardowego powiązania wziąć pod uwagę wymagania dotyczące usługi WSE 3.0 i wymagania współpraca między usługi WSE 3.0 i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta. Te wymagania dotyczące współdziałania obejmują wyżej wymienione korzystanie z sierpnia 2004 specyfikacji WS-Addressing i WSE 3.0default wiadomości ochrony <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. Domyślna ochrona wiadomości dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. W tym temacie szczegółowo przedstawiają, jak utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania, który współdziała z usługi WSE 3.0. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] udostępnia również próbki, która będzie zawierała tego powiązania. Aby uzyskać więcej informacji dotyczących tego przykładu, zobacz [współpracy z usługami sieci Web ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Do uzyskania dostępu do usługi sieci Web programu WSE 3.0 za pomocą klienta WCF  
  
1.  Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta usługi sieci Web programu WSE 3.0.  
  
     Usługi sieci Web programu WSE 3.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient jest tworzony. Ponieważ WSE 3.0 nie obsługuje protokołu MEX, nie można użyć narzędzia do pobierania wymagań bezpieczeństwa dla usługi sieci Web. Deweloper aplikacji należy dodać ustawienia zabezpieczeń dla klienta.  
  
     Aby uzyskać więcej informacji o tworzeniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.  
  
     Następujące klasy jest częścią [współpracy z WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) próbki:  
  
    1.  Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.  
  
         Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` która pochodzi z <xref:System.ServiceModel.Channels.Binding> klasy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Dodaj właściwości do klasy, która Określ potwierdzenia gotowe WSE używane przez usługi WSE, czy wymagane są klucze pochodnej, czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości. W WSE 3.0 gotowe potwierdzenia określa wymagania dotyczące zabezpieczeń dla klienta lub usługi sieci Web — podobnie jak tryb uwierzytelniania powiązania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
         Poniższy przykładowy kod definiuje `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, i `MessageProtectionOrder` właściwości, które określają WSE potwierdzenia gotowe, czy kluczy pochodnych są wymagane, czy bezpiecznej sesji są używane, czy podpis potwierdzenia są wymagane i ustawienia ochrony wiadomości, odpowiednio.  
  
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
 Poniższy przykładowy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odpowiadają właściwości potwierdzenia zabezpieczeń gotowe WSE 3.0. Tego niestandardowego powiązania o nazwie `WseHttpBinding`, jest następnie używany do określania właściwości powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który komunikuje się z próbki WSSecurityAnonymous WSE 3.0 — Szybki Start.  
  
  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 [Współdziałanie z WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
