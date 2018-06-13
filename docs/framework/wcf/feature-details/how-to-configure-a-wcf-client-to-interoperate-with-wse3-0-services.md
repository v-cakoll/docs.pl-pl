---
title: 'Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: e30403f9c97f31e93c22a9658ffb74d4d02a49ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490646"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="fa964-102">Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0</span><span class="sxs-lookup"><span data-stu-id="fa964-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="fa964-103">Klientów systemu Windows Communication Foundation (WCF) są zgodny poziom przewodowy z 3.0 rozszerzenia usługi sieci Web dla usług platformy Microsoft .NET (WSE), gdy klienci WCF są skonfigurowane do korzystania z sierpnia 2004 wersja specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="fa964-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="fa964-104">Aby skonfigurować klienta programu WCF na potrzeby współdziałania z usługą sieci Web programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="fa964-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="fa964-105">Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można utworzyć klienta WCF dla usługi sieci Web programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="fa964-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="fa964-106">Dla usługi sieci Web programu WSE tworzony jest klasa klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="fa964-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="fa964-107">Aby uzyskać więcej informacji o tworzeniu klienta WCF, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="fa964-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="fa964-108">Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fa964-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="fa964-109">Następujące klasy jest częścią [współpracy z WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) próbki.</span><span class="sxs-lookup"><span data-stu-id="fa964-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="fa964-110">Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="fa964-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="fa964-111">Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` która pochodzi z <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="fa964-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="fa964-112">Dodaj właściwości do klasy, która określa potwierdzenia gotowe WSE, czy wymagane są klucze pochodnej czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fa964-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="fa964-113">Poniższy przykładowy kod definiuje `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` właściwości, które określają potwierdzenia gotowe WSE, czy wymagane są klucze pochodnej czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="fa964-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="fa964-114">Zastąpienie <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody do ustawiania właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa964-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="fa964-115">Poniższy przykład kodu określa transportu, kodowania wiadomości i ustawienia ochrony wiadomości przez pobieranie wartości z `SecurityAssertion` i `MessageProtectionOrder` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa964-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="fa964-116">W kodzie aplikacji klienta Dodaj kod, aby ustawić właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa964-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="fa964-117">Poniższy przykład kodu Określa, że klient WCF musi używać ochrony wiadomości oraz uwierzytelnianie zgodnie z definicją w WSE 3.0 `AnonymousForCertificate` potwierdzenia zabezpieczeń gotowe.</span><span class="sxs-lookup"><span data-stu-id="fa964-117">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="fa964-118">Ponadto wymagane są bezpieczne sesje i kluczy pochodnych.</span><span class="sxs-lookup"><span data-stu-id="fa964-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="fa964-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa964-119">Example</span></span>  
 <span data-ttu-id="fa964-120">Poniższy przykładowy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odpowiadają właściwości potwierdzenia zabezpieczeń gotowe WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="fa964-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="fa964-121">Wiązanie niestandardowe o nazwie `WseHttpBinding`, jest następnie używany do określania właściwości powiązania dla klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="fa964-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="fa964-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa964-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="fa964-123">Współdziałanie z WSE</span><span class="sxs-lookup"><span data-stu-id="fa964-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
