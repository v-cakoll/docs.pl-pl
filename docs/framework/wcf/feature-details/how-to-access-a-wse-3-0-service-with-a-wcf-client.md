---
title: 'Instrukcje: Dostęp do usługi WSE 3.0 za pomocą klienta programu WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 2e01d3de6ee7b415c7b3f18a20e840b8ec4ab9b6
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508125"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Instrukcje: Dostęp do usługi WSE 3.0 za pomocą klienta programu WCF
Klienci Windows Communication Foundation (WCF) są protokół sieciowy niskiego poziomu zgodnego z sieci Web usługi rozszerzeń (programu WSE) 3.0 dla usług programu Microsoft .NET, gdy klienci WCF są skonfigurowane do korzystania z sierpnia 2004 wersję specyfikacji WS-Addressing. Jednak usługi WSE 3.0 nie obsługują metadanych protokołu exchange (MEX), dlatego podczas korzystania [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia klasy klienta WCF, ustawienia zabezpieczeń nie są stosowane do wygenerowany Klient usługi WCF. W związku z tym, należy określić ustawienia zabezpieczeń, usługa programu WSE 3.0 wymaga po wygenerowaniu klienta platformy WCF.  
  
 Aby zastosować te ustawienia zabezpieczeń, należy wziąć pod uwagę wymagania dotyczące usługi WSE 3.0 i interoperacyjne wymagania między usługą programu WSE 3.0 i klienta programu WCF za pomocą niestandardowego powiązania. Wymagania w zakresie współdziałania obejmują wykorzystanie wyżej sierpnia 2004 specyfikacji WS-Addressing i WSE 3.0default komunikatu ochrony <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. Jest to domyślna ochrona komunikatów WCF <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. W tym temacie przedstawiono sposób tworzenia powiązań WCF, która współdziała z usługą programu WSE 3.0. Usługi WCF zawiera również przykładowy, uwzględniająca tego powiązania. Aby uzyskać więcej informacji na temat tego przykładu, zobacz [współdziałanie z usługami sieci Web ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Do uzyskania dostępu do usługi sieci Web programu WSE 3.0 za pomocą klienta WCF  
  
1.  Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można utworzyć klienta WCF usługi sieci Web programu WSE 3.0.  
  
     W przypadku usługi sieci Web programu WSE 3.0 klienta WCF jest tworzony. Ponieważ programu WSE 3.0 nie obsługuje protokół wymiany Metadanych, nie można użyć narzędzia do pobierania wymagania dotyczące zabezpieczeń dla usługi sieci Web. Deweloper aplikacji należy dodać ustawienia zabezpieczeń dla klienta.  
  
     Aby uzyskać więcej informacji na temat tworzenia klienta WCF, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.  
  
     Następujące klasy jest częścią [współdziałanie z usługami WSE](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) próbki:  
  
    1.  Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.  
  
         Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` który pochodzi od klasy <xref:System.ServiceModel.Channels.Binding> klasy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Dodaj właściwości do klasy, określające potwierdzenie gotowej do użycia programu WSE używane przez usługi WSE, czy pochodne klucze są wymagane, czy bezpiecznych sesji są używane, czy wymagane są potwierdzenia podpisu i ustawienia ochrony wiadomości. W programu WSE 3.0, gotową do użycia potwierdzenia określa wymagania dotyczące zabezpieczeń dla klienta lub usługi sieci Web — podobnie jak tryb uwierzytelniania powiązania programu WCF.  
  
         Poniższy przykład kodu przedstawia `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, i `MessageProtectionOrder` właściwości, które określają WSE gotowej do użycia potwierdzenia, czy pochodne klucze są wymagane, czy bezpiecznych sesji są używane, czy podpis potwierdzenia są wymagane i ustawienia ochrony wiadomości, odpowiednio.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Zastąp <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodę, aby ustawić właściwości powiązania.  
  
         Poniższy przykład kodu określa transportu, kodowania wiadomości i ustawienia ochrony wiadomości przez pobranie wartości `SecurityAssertion` i `MessageProtectionOrder` właściwości.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  W kodzie aplikacji klienta należy dodać kod, aby ustawić właściwości powiązania.  
  
     Poniższy przykład kodu Określa, że klienta platformy WCF musi używać ochrony wiadomości i uwierzytelniania, zgodnie z definicją programu WSE 3.0 `AnonymousForCertificate` asercji zabezpieczeń gotowej do użycia. Ponadto wymagane są bezpieczne sesje i kluczy pochodnych.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odnoszą się do właściwości asercji zabezpieczeń gotowej do użycia programu WSE 3.0. Tego niestandardowego powiązania, który nosi nazwę `WseHttpBinding`, jest następnie używany do określania właściwości powiązania klienta WCF, który komunikuje się z przykładem WSSecurityAnonymous programu WSE 3.0 przewodnik Szybki Start.  
  
  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 [Współdziałanie z usługami WSE](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
