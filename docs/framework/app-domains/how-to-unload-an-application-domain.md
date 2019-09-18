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
ms.openlocfilehash: f7419725f3822622a8e4210d4f3f5d8e9e59dbdd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053132"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="df807-102">Instrukcje: Zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="df807-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="df807-103">Po zakończeniu korzystania z domeny aplikacji zwolnij ją przy użyciu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="df807-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="df807-104">Metoda **Unload** bezpiecznie zamyka określoną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df807-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="df807-105">W trakcie procesu zwalniania żadne nowe wątki nie mogą uzyskać dostępu do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwolnione.</span><span class="sxs-lookup"><span data-stu-id="df807-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="df807-106">Zestawy ładowane do domeny aplikacji są usuwane i nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="df807-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="df807-107">Jeśli zestaw w domenie aplikacji jest niezależny od domeny, dane dla zestawu pozostają w pamięci, dopóki cały proces nie zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="df807-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="df807-108">Nie istnieje mechanizm zwalniania zestawu neutralnego z domeną poza zamknięciem całego procesu.</span><span class="sxs-lookup"><span data-stu-id="df807-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="df807-109">Istnieją sytuacje, w których żądanie zwolnienia domeny aplikacji nie działa i daje w wyniku <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="df807-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="df807-110">Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`, drukuje pewne informacje w konsoli, a następnie zwalnia domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df807-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="df807-111">Należy zauważyć, że kod próbuje wydrukować przyjazną nazwę nieładowanej domeny aplikacji do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="df807-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="df807-112">Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje try/catch na końcu programu.</span><span class="sxs-lookup"><span data-stu-id="df807-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df807-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="df807-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="df807-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df807-114">See also</span></span>

- [<span data-ttu-id="df807-115">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="df807-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="df807-116">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="df807-116">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="df807-117">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="df807-117">Using Application Domains</span></span>](use.md)
