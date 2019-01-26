---
title: 'Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 345677f992491022a12fb03981f644343e405dfe
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066457"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="52572-102">Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0</span><span class="sxs-lookup"><span data-stu-id="52572-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="52572-103">Klienci Windows Communication Foundation (WCF) są zgodne protokół sieciowy niskiego poziomu z rozszerzeń usługi sieci Web w wersji 3.0 dla usług programu Microsoft .NET (WSE), gdy klienci WCF są skonfigurowane do korzystania z sierpnia 2004 wersję specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="52572-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="52572-104">Aby skonfigurować klienta programu WCF do współdziałania z usługą sieci Web programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="52572-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="52572-105">Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można utworzyć klienta WCF usługi sieci Web programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="52572-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="52572-106">Dla usługi sieci Web programu WSE tworzony jest klasa klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="52572-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="52572-107">Aby uzyskać szczegółowe informacje o tworzeniu klienta WCF, zobacz [jak: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="52572-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="52572-108">Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="52572-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="52572-109">Następujące klasy jest częścią [współdziałanie z usługami WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) próbki.</span><span class="sxs-lookup"><span data-stu-id="52572-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1.  <span data-ttu-id="52572-110">Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="52572-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="52572-111">Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` który pochodzi od klasy <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="52572-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="52572-112">Dodaj właściwości do klasy, określające potwierdzenie gotowej do użycia programu WSE, czy pochodne klucze są wymagane, czy bezpiecznych sesji są używane, czy wymagane są potwierdzenia podpisu i ustawienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="52572-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="52572-113">Poniższy przykład kodu przedstawia `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, i `MessageProtectionOrder` właściwości.</span><span class="sxs-lookup"><span data-stu-id="52572-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="52572-114">Odpowiednio określają potwierdzenie gotowej do użycia programu WSE, czy pochodne klucze są wymagane, czy bezpiecznych sesji są używane, czy wymagane są potwierdzenia podpisu i ustawienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="52572-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="52572-115">Zastąp <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodę, aby ustawić właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="52572-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="52572-116">Poniższy przykład kodu określa transportu, kodowania wiadomości i ustawienia ochrony wiadomości przez pobranie wartości `SecurityAssertion` i `MessageProtectionOrder` właściwości.</span><span class="sxs-lookup"><span data-stu-id="52572-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="52572-117">W kodzie aplikacji klienta należy dodać kod, aby ustawić właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="52572-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="52572-118">Poniższy przykład kodu Określa, że klienta platformy WCF musi używać ochrony wiadomości i uwierzytelniania, zgodnie z definicją programu WSE 3.0 `AnonymousForCertificate` asercji zabezpieczeń gotowej do użycia.</span><span class="sxs-lookup"><span data-stu-id="52572-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="52572-119">Ponadto wymagane są bezpieczne sesje i kluczy pochodnych.</span><span class="sxs-lookup"><span data-stu-id="52572-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="52572-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="52572-120">Example</span></span>  
 <span data-ttu-id="52572-121">Poniższy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odnoszą się do właściwości asercji zabezpieczeń gotowej do użycia programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="52572-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="52572-122">Niestandardowe powiązanie, które nosi nazwę `WseHttpBinding`, jest następnie używany do określania właściwości powiązania dla klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="52572-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="52572-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52572-123">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="52572-124">Współdziałanie z usługami WSE</span><span class="sxs-lookup"><span data-stu-id="52572-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
