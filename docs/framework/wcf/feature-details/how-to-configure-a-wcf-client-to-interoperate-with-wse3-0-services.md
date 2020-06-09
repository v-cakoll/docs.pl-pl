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
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="17078-102">Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0</span><span class="sxs-lookup"><span data-stu-id="17078-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="17078-103">Klienci korzystający z programu Windows Communication Foundation (WCF) są zgodną z usługami sieci Web udoskonalenia 3,0 dla usług Microsoft .NET (WSE), gdy klienci WCF są skonfigurowani do korzystania z wersji z sierpnia 2004 specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="17078-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="17078-104">Aby skonfigurować klienta WCF do współdziałania z usługą sieci Web WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="17078-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="17078-105">Uruchom narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , aby utworzyć klienta WCF dla usługi sieci Web WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="17078-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="17078-106">W przypadku usługi sieci Web WSE tworzona jest Klasa klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="17078-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="17078-107">Aby uzyskać szczegółowe informacje o tworzeniu klienta WCF, zobacz [How to: Create a Client](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="17078-107">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="17078-108">Utwórz klasę, która reprezentuje powiązanie, które może komunikować się z usługami sieci Web WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="17078-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="17078-109">Następująca Klasa jest częścią [współdziałania z](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) przykładem WSE.</span><span class="sxs-lookup"><span data-stu-id="17078-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1. <span data-ttu-id="17078-110">Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="17078-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="17078-111">Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` , która dziedziczy z <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="17078-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="17078-112">Dodaj właściwości do klasy, która określa WSE gotowe, bez względu na to, czy klucze pochodne są wymagane, czy są używane bezpieczne sesje, czy potwierdzania podpisu są wymagane oraz ustawienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="17078-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="17078-113">Poniższy przykład kodu definiuje `SecurityAssertion` właściwości,, `RequireDerivedKeys` `EstablishSecurityContext` i `MessageProtectionOrder` .</span><span class="sxs-lookup"><span data-stu-id="17078-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="17078-114">Określają one WSE gotowe, niezależnie od tego, czy klucze pochodne są wymagane, czy są używane bezpieczne sesje, czy potwierdzenia podpisu są wymagane i odpowiednio ustawienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="17078-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="17078-115">Zastąp <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodę, aby ustawić właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="17078-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="17078-116">Poniższy przykład kodu określa ustawienia transportu, kodowania komunikatów i ochrony wiadomości, pobierając wartości `SecurityAssertion` `MessageProtectionOrder` właściwości i.</span><span class="sxs-lookup"><span data-stu-id="17078-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="17078-117">W kodzie aplikacji klienckiej Dodaj kod, aby ustawić właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="17078-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="17078-118">Poniższy przykład kodu określa, że klient WCF musi używać ochrony komunikatów i uwierzytelniania zgodnie z opisem w `AnonymousForCertificate` potwierdzeniu zabezpieczeń WSE 3,0 gotowe.</span><span class="sxs-lookup"><span data-stu-id="17078-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="17078-119">Dodatkowo wymagane są bezpieczne sesje i klucze pochodne.</span><span class="sxs-lookup"><span data-stu-id="17078-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="17078-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="17078-120">Example</span></span>  
 <span data-ttu-id="17078-121">Poniższy przykład kodu definiuje niestandardowe powiązanie, które uwidacznia właściwości odpowiadające właściwościom WSE 3,0 gotowe Security Assertion.</span><span class="sxs-lookup"><span data-stu-id="17078-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="17078-122">Niestandardowe powiązanie o nazwie jest `WseHttpBinding` następnie używane do określania właściwości powiązań dla klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="17078-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="17078-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17078-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="17078-124">Współdziałanie z WSE</span><span class="sxs-lookup"><span data-stu-id="17078-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
