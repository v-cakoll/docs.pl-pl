---
title: 'Instrukcje: Zwolnienie domeny aplikacji'
description: Przeczytaj, jak zwolnić domenę aplikacji w programie .NET przy użyciu metody AppDomain. Unload, aby bezpiecznie zamknąć określoną domenę aplikacji.
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
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104676"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="e63e7-103">Instrukcje: Zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e63e7-103">How to: Unload an Application Domain</span></span>
<span data-ttu-id="e63e7-104">Po zakończeniu korzystania z domeny aplikacji zwolnij ją przy użyciu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e63e7-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e63e7-105">Metoda **Unload** bezpiecznie zamyka określoną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e63e7-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="e63e7-106">W trakcie procesu zwalniania żadne nowe wątki nie mogą uzyskać dostępu do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwolnione.</span><span class="sxs-lookup"><span data-stu-id="e63e7-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="e63e7-107">Zestawy ładowane do domeny aplikacji są usuwane i nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="e63e7-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="e63e7-108">Jeśli zestaw w domenie aplikacji jest niezależny od domeny, dane dla zestawu pozostają w pamięci, dopóki cały proces nie zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="e63e7-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="e63e7-109">Nie istnieje mechanizm zwalniania zestawu neutralnego z domeną poza zamknięciem całego procesu.</span><span class="sxs-lookup"><span data-stu-id="e63e7-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="e63e7-110">Istnieją sytuacje, w których żądanie zwolnienia domeny aplikacji nie działa i daje w wyniku <xref:System.CannotUnloadAppDomainException> .</span><span class="sxs-lookup"><span data-stu-id="e63e7-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="e63e7-111">Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain` , drukuje pewne informacje w konsoli, a następnie zwalnia domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e63e7-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="e63e7-112">Należy zauważyć, że kod próbuje wydrukować przyjazną nazwę nieładowanej domeny aplikacji do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="e63e7-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="e63e7-113">Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje try/catch na końcu programu.</span><span class="sxs-lookup"><span data-stu-id="e63e7-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e63e7-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e63e7-114">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e63e7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e63e7-115">See also</span></span>

- [<span data-ttu-id="e63e7-116">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="e63e7-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="e63e7-117">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e63e7-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="e63e7-118">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e63e7-118">Using Application Domains</span></span>](use.md)
