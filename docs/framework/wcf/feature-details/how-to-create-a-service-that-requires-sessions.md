---
title: 'Instrukcje: Tworzenie usługi wymagającej użycia sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184990"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="fe02e-102">Instrukcje: Tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="fe02e-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="fe02e-103">Sesje utworzyć stan udostępniony między dwoma lub więcej punktów końcowych, który umożliwia przydatne funkcje, takie jak wywołania zwrotne, zabezpieczenia wielu przeskoków i skojarzenia między klientami i wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="fe02e-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="fe02e-104">Aby uzyskać więcej informacji na temat sesji w aplikacjach Windows Communication Foundation (WCF), zobacz [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="fe02e-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="fe02e-105">Aby określić, że umowa wymaga jej powiązania do obsługi sesji</span><span class="sxs-lookup"><span data-stu-id="fe02e-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="fe02e-106">Utwórz umowę serwisową przy czym jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="fe02e-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="fe02e-107">Na przykład jak utworzyć umowę serwisową, zobacz [Jak: Definiowanie umowy serwisowej](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="fe02e-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="fe02e-108">Zmodyfikuj, <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> który <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> deklaruje kontrakt, ustawiając właściwość na jedną z:</span><span class="sxs-lookup"><span data-stu-id="fe02e-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="fe02e-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>jeśli umowa ta musi być uruchamiana w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="fe02e-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="fe02e-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>jeśli ten kontrakt może być uruchomiony w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="fe02e-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="fe02e-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>jeśli umowa ta nie może być uruchamiana w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="fe02e-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="fe02e-112">Skonfiguruj punkt końcowy usługi, aby używać powiązania, które obsługuje sesje.</span><span class="sxs-lookup"><span data-stu-id="fe02e-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="fe02e-113">Poniższy przykład konfiguracji pokazuje <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>użycie programu ,`-`który obsługuje sesję WS ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="fe02e-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="fe02e-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe02e-114">Example</span></span>  
 <span data-ttu-id="fe02e-115">Poniższy przykładowy kod pokazuje, jak określić wymagania dotyczące sesji na poziomie <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> kontraktu i użyć pliku konfiguracji do obsługi tego wymagania z powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="fe02e-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="fe02e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe02e-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
