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
ms.openlocfilehash: ea71737e1e214aa1a035739901bf79f8ef4a9c7a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="51db9-102">Instrukcje: Konfigurowanie klienta programu WCF do współdziałania z usługami WES3.0</span><span class="sxs-lookup"><span data-stu-id="51db9-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="51db9-103">Klienci są przewodowy poziom zgodny z 3.0 rozszerzenia usługi sieci Web dla usług platformy Microsoft .NET (WSE), kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów są skonfigurowane do korzystania z sierpnia 2004 wersja specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="51db9-103"> clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="51db9-104">Aby skonfigurować klienta programu WCF na potrzeby współdziałania z usługą sieci Web programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="51db9-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="51db9-105">Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta usługi sieci Web programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db9-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="51db9-106">Usługi sieci Web programu WSE [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utworzeniu klasy klienta.</span><span class="sxs-lookup"><span data-stu-id="51db9-106">For a WSE Web service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class is created.</span></span>  
  
     <span data-ttu-id="51db9-107">Aby uzyskać więcej informacji o tworzeniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="51db9-107">For details about creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="51db9-108">Utwórz klasę, która reprezentuje powiązanie, który może komunikować się z usługami WSE 3.0 w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="51db9-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="51db9-109">Następujące klasy jest częścią [współpracy z WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) próbki.</span><span class="sxs-lookup"><span data-stu-id="51db9-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="51db9-110">Utwórz klasę pochodną od klasy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="51db9-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="51db9-111">Poniższy przykład kodu tworzy klasę o nazwie `WseHttpBinding` która pochodzi z <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="51db9-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="51db9-112">Dodaj właściwości do klasy, która określa potwierdzenia gotowe WSE, czy wymagane są klucze pochodnej czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="51db9-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="51db9-113">Poniższy przykładowy kod definiuje `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` właściwości, które określają potwierdzenia gotowe WSE, czy wymagane są klucze pochodnej czy bezpiecznej sesji są używane, czy są wymagane potwierdzenie podpisu i ustawienia ochrony wiadomości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="51db9-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="51db9-114">Zastąpienie <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody do ustawiania właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="51db9-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="51db9-115">Poniższy przykład kodu określa transportu, kodowania wiadomości i ustawienia ochrony wiadomości przez pobieranie wartości z `SecurityAssertion` i `MessageProtectionOrder` właściwości.</span><span class="sxs-lookup"><span data-stu-id="51db9-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="51db9-116">W kodzie aplikacji klienta Dodaj kod, aby ustawić właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="51db9-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="51db9-117">Poniższy przykład kodu Określa, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta musi używać uwierzytelniania i ochrony wiadomości, zgodnie z definicją w WSE 3.0 `AnonymousForCertificate` potwierdzenia zabezpieczeń gotowe.</span><span class="sxs-lookup"><span data-stu-id="51db9-117">The following code example specifies that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="51db9-118">Ponadto wymagane są bezpieczne sesje i kluczy pochodnych.</span><span class="sxs-lookup"><span data-stu-id="51db9-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="51db9-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="51db9-119">Example</span></span>  
 <span data-ttu-id="51db9-120">Poniższy przykładowy kod definiuje niestandardowego powiązania, który udostępnia właściwości, które odpowiadają właściwości potwierdzenia zabezpieczeń gotowe WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db9-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="51db9-121">Wiązanie niestandardowe o nazwie `WseHttpBinding`, jest następnie używany do określania właściwości powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="51db9-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="51db9-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51db9-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="51db9-123">Współdziałanie z WSE</span><span class="sxs-lookup"><span data-stu-id="51db9-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
