---
title: 'Porady: zwolnienie domeny aplikacji'
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
ms.openlocfilehash: 4d5f98229c3a9da69a350ae325cd42e8deb6b7bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119845"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="d3f9b-102">Porady: zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3f9b-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="d3f9b-103">Po zakończeniu korzystania z domeny aplikacji zwolnij ją przy użyciu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d3f9b-104">Metoda **Unload** bezpiecznie zamyka określoną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="d3f9b-105">W trakcie procesu zwalniania żadne nowe wątki nie mogą uzyskać dostępu do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwolnione.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="d3f9b-106">Zestawy ładowane do domeny aplikacji są usuwane i nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="d3f9b-107">Jeśli zestaw w domenie aplikacji jest niezależny od domeny, dane dla zestawu pozostają w pamięci, dopóki cały proces nie zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="d3f9b-108">Nie istnieje mechanizm zwalniania zestawu neutralnego z domeną poza zamknięciem całego procesu.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="d3f9b-109">Istnieją sytuacje, w których żądanie zwolnienia domeny aplikacji nie działa i daje w wyniku <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="d3f9b-110">Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`, drukuje pewne informacje w konsoli, a następnie zwalnia domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="d3f9b-111">Należy zauważyć, że kod próbuje wydrukować przyjazną nazwę nieładowanej domeny aplikacji do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="d3f9b-112">Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje try/catch na końcu programu.</span><span class="sxs-lookup"><span data-stu-id="d3f9b-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f9b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3f9b-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d3f9b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3f9b-114">See also</span></span>

- [<span data-ttu-id="d3f9b-115">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3f9b-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="d3f9b-116">Porady: tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3f9b-116">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="d3f9b-117">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3f9b-117">Using Application Domains</span></span>](use.md)
