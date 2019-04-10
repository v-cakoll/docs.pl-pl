---
title: 'Instrukcje: Zwolnienie domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3011bd0327440cd04d5eccf5f88c036ddd76267
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212183"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="8a2a6-102">Instrukcje: Zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8a2a6-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="8a2a6-103">Po zakończeniu, przy użyciu domeny aplikacji, zwolnij go za pomocą <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8a2a6-104">**Zwolnienie** metody bez problemu zmieniała wyłączania domeny określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="8a2a6-105">W trakcie zwalniania żadne nowe wątki mogą uzyskiwać dostęp do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwalniane.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="8a2a6-106">Zestawy, ładowane do domeny aplikacji zostaną usunięte i nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="8a2a6-107">Jeśli zestaw w domenie aplikacji jest niezależne od domeny, dane dla zestawu pozostaje w pamięci, dopóki nie zostanie zamknięta przez cały proces.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="8a2a6-108">Nie ma mechanizmu zwolnić zestaw niezależne od domeny inne niż zamykanie cały proces.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="8a2a6-109">Istnieją sytuacje, gdy żądanie zwolnienie domeny aplikacji nie będzie działać, a wynikiem <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="8a2a6-110">Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`drukuje pewnych informacji w konsoli i następnie zwalnia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="8a2a6-111">Należy pamiętać, że kod jest podejmuje próbę drukowania przyjazna nazwa niezaładowanej domenie aplikacji w konsoli.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="8a2a6-112">Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje bloku try/catch na końcu program.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a2a6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2a6-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8a2a6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a2a6-114">See also</span></span>

- [<span data-ttu-id="8a2a6-115">Programowanie za pomocą domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="8a2a6-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="8a2a6-116">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8a2a6-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [<span data-ttu-id="8a2a6-117">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8a2a6-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
