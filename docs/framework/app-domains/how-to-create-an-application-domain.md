---
title: 'Instrukcje: Tworzenie domeny aplikacji'
description: Zapoznaj się z tematem jak utworzyć domenę aplikacji w programie .NET. Możesz utworzyć domenę aplikacji, aby załadować zestawy do zarządzania osobiście, lub utwórz je do wykonania kodu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104812"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="c8abe-104">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8abe-104">How to: Create an Application Domain</span></span>
<span data-ttu-id="c8abe-105">Host środowiska uruchomieniowego języka wspólnego automatycznie tworzy domeny aplikacji, gdy są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="c8abe-105">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="c8abe-106">Można jednak tworzyć własne domeny aplikacji i ładować je do tych zestawów, które mają być zarządzane osobiście.</span><span class="sxs-lookup"><span data-stu-id="c8abe-106">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="c8abe-107">Możesz również utworzyć domeny aplikacji, z których wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="c8abe-107">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="c8abe-108">Tworzysz nową domenę aplikacji przy użyciu jednej **z przeciążonych** metod w <xref:System.AppDomain?displayProperty=nameWithType> klasie.</span><span class="sxs-lookup"><span data-stu-id="c8abe-108">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c8abe-109">Możesz nadać domenie aplikacji nazwę i odwołać się do niej przy użyciu tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c8abe-109">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="c8abe-110">Poniższy przykład tworzy nową domenę aplikacji, przypisuje jej nazwę `MyDomain` , a następnie drukuje nazwę domeny hosta i nowo utworzoną domenę podrzędnej aplikacji do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="c8abe-110">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8abe-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8abe-111">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c8abe-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8abe-112">See also</span></span>

- [<span data-ttu-id="c8abe-113">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8abe-113">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="c8abe-114">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8abe-114">Using Application Domains</span></span>](use.md)
