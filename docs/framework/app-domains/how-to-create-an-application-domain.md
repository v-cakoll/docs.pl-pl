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
ms.openlocfilehash: 7f42f85adf3e9b0874df6c0360bea25b07facc0d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053161"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="ccbe2-102">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ccbe2-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="ccbe2-103">Host środowiska uruchomieniowego języka wspólnego automatycznie tworzy domeny aplikacji, gdy są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ccbe2-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="ccbe2-104">Można jednak tworzyć własne domeny aplikacji i ładować je do tych zestawów, które mają być zarządzane osobiście.</span><span class="sxs-lookup"><span data-stu-id="ccbe2-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="ccbe2-105">Możesz również utworzyć domeny aplikacji, z których wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="ccbe2-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="ccbe2-106">Tworzysz nową domenę aplikacji przy użyciu jednej **z przeciążonych** metod w <xref:System.AppDomain?displayProperty=nameWithType> klasie.</span><span class="sxs-lookup"><span data-stu-id="ccbe2-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ccbe2-107">Możesz nadać domenie aplikacji nazwę i odwołać się do niej przy użyciu tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ccbe2-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="ccbe2-108">Poniższy przykład tworzy nową domenę aplikacji, przypisuje jej nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i nowo utworzoną domenę podrzędnej aplikacji do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="ccbe2-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccbe2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccbe2-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ccbe2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccbe2-110">See also</span></span>

- [<span data-ttu-id="ccbe2-111">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ccbe2-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="ccbe2-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ccbe2-112">Using Application Domains</span></span>](use.md)
