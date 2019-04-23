---
title: 'Instrukcje: Tworzenie domeny aplikacji'
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
ms.openlocfilehash: ff85f5737babb73d87f4918ca0f4981263f7dadc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166754"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="f24b4-102">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f24b4-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="f24b4-103">Typowe host środowiska uruchomieniowego języka automatycznie tworzy domen aplikacji, gdy są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="f24b4-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="f24b4-104">Można jednak tworzenie domen aplikacji i ładowania ich te zestawy, które mają być zarządzane osobiście.</span><span class="sxs-lookup"><span data-stu-id="f24b4-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="f24b4-105">Można również utworzyć domen aplikacji, z których wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="f24b4-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="f24b4-106">Tworzenie nowej domeny aplikacji przy użyciu jednej z przeciążonych **createdomain —** metody <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="f24b4-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f24b4-107">Można podać nazwę domeny aplikacji i odwoływać się do niego o takiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f24b4-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="f24b4-108">Poniższy przykład tworzy nową domenę aplikacji, przypisuje mu nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i domeny aplikacji nowo utworzony do konsoli.</span><span class="sxs-lookup"><span data-stu-id="f24b4-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f24b4-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f24b4-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f24b4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f24b4-110">See also</span></span>

- [<span data-ttu-id="f24b4-111">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="f24b4-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="f24b4-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="f24b4-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
