---
title: 'Porady: tworzenie domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95e5bdbeda4f6faff33467233e28d9dd6bc01d1c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186936"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="ab292-102">Porady: tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab292-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="ab292-103">Typowe host środowiska uruchomieniowego języka automatycznie tworzy domen aplikacji, gdy są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ab292-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="ab292-104">Można jednak tworzenie domen aplikacji i ładowania ich te zestawy, które mają być zarządzane osobiście.</span><span class="sxs-lookup"><span data-stu-id="ab292-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="ab292-105">Można również utworzyć domen aplikacji, z których wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="ab292-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="ab292-106">Tworzenie nowej domeny aplikacji przy użyciu jednej z przeciążonych **createdomain —** metody <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab292-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ab292-107">Można podać nazwę domeny aplikacji i odwoływać się do niego o takiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ab292-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="ab292-108">Poniższy przykład tworzy nową domenę aplikacji, przypisuje mu nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i domeny aplikacji nowo utworzony do konsoli.</span><span class="sxs-lookup"><span data-stu-id="ab292-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab292-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab292-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ab292-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab292-110">See Also</span></span>  
- [<span data-ttu-id="ab292-111">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab292-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
- [<span data-ttu-id="ab292-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab292-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
