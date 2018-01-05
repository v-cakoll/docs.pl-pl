---
title: 'Porady: tworzenie domeny aplikacji'
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
helpviewer_keywords: application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e17b4d542206deadf960234cfe1091896ab5f92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="4c1eb-102">Porady: tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4c1eb-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="4c1eb-103">Typowe host czasu wykonywania języka automatycznie tworzy domeny aplikacji, gdy są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="4c1eb-104">Można jednak tworzenie domeny aplikacji i załadować do nich te zestawy, które mają być zarządzane osobiście.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="4c1eb-105">Można też utworzyć, z których wykonanie kodu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="4c1eb-106">Tworzenie nowej domeny aplikacji przy użyciu jednej z przeciążone **CreateDomain** metod w <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4c1eb-107">Należy podać nazwę domeny aplikacji i odwołaj się o takiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="4c1eb-108">Poniższy przykład tworzy nową domenę aplikacji, przypisuje mu nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i domeny podrzędnej nowo utworzonej aplikacji do konsoli.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c1eb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c1eb-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4c1eb-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c1eb-110">See Also</span></span>  
 [<span data-ttu-id="4c1eb-111">Programowanie za pomocą domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4c1eb-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="4c1eb-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="4c1eb-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
