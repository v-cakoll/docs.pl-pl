---
title: "Porady: ładowanie i zwalnianie zestawów (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="e8e06-102">Porady: ładowanie i zwalnianie zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="e8e06-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="e8e06-103">Zestawy odwołuje się program automatycznie zostaną załadowane w czasie kompilacji, ale jest również możliwe ładowanie określonych zestawów do bieżącej domeny aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e8e06-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="e8e06-104">Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="e8e06-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="e8e06-105">Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces.</span><span class="sxs-lookup"><span data-stu-id="e8e06-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="e8e06-106">Nawet wtedy, gdy zestaw wykracza poza zakres, plik zestawu rzeczywiste pozostanie załadować dopóki wszystkie domeny aplikacji, które zawierałoby proces są usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8e06-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="e8e06-107">Aby zwolnić niektóre zestawy, a innych nie, należy rozważyć tworzenia nowej domeny aplikacji, wykonywanie kodu w tej domenie i następnie zwalnianie tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8e06-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="e8e06-108">Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="e8e06-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="e8e06-109">Aby załadować zestawu do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e8e06-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="e8e06-110">Użyj załadować jedną z kilku metod zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="e8e06-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="e8e06-111">Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="e8e06-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="e8e06-112">Aby zwolnić domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e8e06-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="e8e06-113">Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces.</span><span class="sxs-lookup"><span data-stu-id="e8e06-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="e8e06-114">Użyj `Unload` metody z <xref:System.AppDomain> można zwolnić domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8e06-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="e8e06-115">Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="e8e06-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e06-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8e06-116">See Also</span></span>  
 [<span data-ttu-id="e8e06-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e8e06-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e8e06-118">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="e8e06-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="e8e06-119">Porady: ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e8e06-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
