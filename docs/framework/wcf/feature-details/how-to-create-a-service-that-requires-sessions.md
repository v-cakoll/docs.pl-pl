---
title: 'Instrukcje: Tworzenie usługi, która wymaga użycia sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: fa151d472dbd27a62f91cd3a43339c66787dc456
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615445"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="2ab6f-102">Instrukcje: Tworzenie usługi, która wymaga użycia sesji</span><span class="sxs-lookup"><span data-stu-id="2ab6f-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="2ab6f-103">Sesje, Tworzenie udostępnionego stanu między co najmniej dwa punkty końcowe, które umożliwia przydatnych funkcji, takich jak wywołania zwrotne z wieloma przeskokami zabezpieczeń i skojarzenia między klientami a wystąpieniami usługi.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="2ab6f-104">Aby uzyskać więcej informacji o sesji w aplikacji Windows Communication Foundation (WCF), zobacz [przy użyciu sesji](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="2ab6f-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="2ab6f-105">Aby określić, że kontrakt wymaga jej powiązania do obsługi sesji</span><span class="sxs-lookup"><span data-stu-id="2ab6f-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="2ab6f-106">Tworzenie kontraktu usługi za pomocą co najmniej jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="2ab6f-107">Na przykład sposobu tworzenia kontraktu usługi zobacz [jak: Definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="2ab6f-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="2ab6f-108">Modyfikowanie <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> określa kontrakt, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości albo:</span><span class="sxs-lookup"><span data-stu-id="2ab6f-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="2ab6f-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Jeśli ten kontrakt musi być uruchamiane w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="2ab6f-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Jeśli ten kontrakt mogą być uruchamiane w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="2ab6f-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Jeśli nie wolno uruchamiać tej Umowy w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="2ab6f-112">Konfigurowanie punktu końcowego usługi do użycia powiązanie, które obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="2ab6f-113">W poniższym przykładzie konfiguracji prezentuje sposób użycia <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, które obsługuje WS`-`ReliableMessaging sesji.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="2ab6f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ab6f-114">Example</span></span>  
 <span data-ttu-id="2ab6f-115">Poniższy przykład kodu pokazuje, jak określić wymaganie sesji poziomie umowy i przy użyciu pliku konfiguracji w celu spełnienia tego wymagania, za pomocą <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> powiązania.</span><span class="sxs-lookup"><span data-stu-id="2ab6f-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="2ab6f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ab6f-116">See also</span></span>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
