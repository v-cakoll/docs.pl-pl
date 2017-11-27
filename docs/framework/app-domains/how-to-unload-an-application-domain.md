---
title: 'Porady: zwolnienie domeny aplikacji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58fd1477715bafa4e3455a3e476acbae3a098dbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="845f2-102">Porady: zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="845f2-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="845f2-103">Po zakończeniu przy użyciu domeny aplikacji zwolnić ją przy użyciu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="845f2-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="845f2-104">**Zwolnienie** — metoda zamyka bezpieczne domeny określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="845f2-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="845f2-105">Podczas zwalniania nie ma nowych wątków mogą uzyskiwać dostęp do domeny aplikacji i są zwalniane wszystkie struktury dane specyficzne dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="845f2-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="845f2-106">Zestawy ładowane do domeny aplikacji zostaną usunięte i nie będą już dostępne.</span><span class="sxs-lookup"><span data-stu-id="845f2-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="845f2-107">Jeśli zestawu w domenie aplikacji jest neutralne dla domen, danych dla zestawu pozostaje w pamięci, dopóki nie zostanie zamknięta przez cały proces.</span><span class="sxs-lookup"><span data-stu-id="845f2-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="845f2-108">Nie istnieje mechanizm zwolnić zestawem neutralne dla domen innych niż zamykanie cały proces.</span><span class="sxs-lookup"><span data-stu-id="845f2-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="845f2-109">Istnieją sytuacje, gdy żądanie do wyładować domeny aplikacji nie będzie działać, a powoduje <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="845f2-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="845f2-110">Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`, drukuje niektóre informacje w konsoli, a następnie zwalnia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="845f2-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="845f2-111">Należy pamiętać, że kod podejmuje próbę drukowania przyjazną nazwę domeny zwolniony aplikacji do konsoli.</span><span class="sxs-lookup"><span data-stu-id="845f2-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="845f2-112">Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcji try/catch w końcu program.</span><span class="sxs-lookup"><span data-stu-id="845f2-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="845f2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="845f2-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="845f2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="845f2-114">See Also</span></span>  
 [<span data-ttu-id="845f2-115">Programowanie za pomocą domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="845f2-115">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="845f2-116">Porady: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="845f2-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [<span data-ttu-id="845f2-117">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="845f2-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
