---
title: 'Instrukcje: konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 62642651516274a27c44abfc19e94dc529690ea9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304548"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Instrukcje: konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0
Klienci Windows Communication Foundation (WCF) są zgodne protokół sieciowy niskiego poziomu z rozszerzeń usługi sieci Web w wersji 3.0 dla usług programu Microsoft .NET (WSE), gdy klienci WCF są skonfigurowane do korzystania z sierpnia 2004 wersję specyfikacji WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Aby skonfigurować klienta programu WCF do współdziałania z usługą sieci Web programu WSE 3.0  
  
1. Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można utworzyć klienta WCF usługi sieci Web programu WSE 3.0.  
  
     Dla usługi sieci Web programu WSE tworzony jest klasa klienta programu WCF.  
  
     Aby uzyskać szczegółowe informacje o tworzeniu klienta WCF, zobacz [jak: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2. Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.  
  
     Następujące klasy jest częścią [współdziałanie z usługami WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) próbki.  
  
    1.  Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.  
  
         Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` który pochodzi od klasy <xref:System.ServiceModel.Channels.Binding> klasy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Dodaj właściwości do klasy, określające potwierdzenie gotowej do użycia programu WSE, czy pochodne klucze są wymagane, czy bezpiecznych sesji są używane, czy wymagane są potwierdzenia podpisu i ustawienia ochrony wiadomości.  
  
         Poniższy przykład kodu przedstawia `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, i `MessageProtectionOrder` właściwości. Odpowiednio określają potwierdzenie gotowej do użycia programu WSE, czy pochodne klucze są wymagane, czy bezpiecznych sesji są używane, czy wymagane są potwierdzenia podpisu i ustawienia ochrony wiadomości.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Zastąp <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodę, aby ustawić właściwości powiązania.  
  
         Poniższy przykład kodu określa transportu, kodowania wiadomości i ustawienia ochrony wiadomości przez pobranie wartości `SecurityAssertion` i `MessageProtectionOrder` właściwości.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. W kodzie aplikacji klienta należy dodać kod, aby ustawić właściwości powiązania.  
  
     Poniższy przykład kodu Określa, że klienta platformy WCF musi używać ochrony wiadomości i uwierzytelniania, zgodnie z definicją programu WSE 3.0 `AnonymousForCertificate` asercji zabezpieczeń gotowej do użycia. Ponadto wymagane są bezpieczne sesje i kluczy pochodnych.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odnoszą się do właściwości asercji zabezpieczeń gotowej do użycia programu WSE 3.0. Niestandardowe powiązanie, które nosi nazwę `WseHttpBinding`, jest następnie używany do określania właściwości powiązania dla klienta programu WCF.  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.Binding>
- [Współdziałanie z usługami WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
