---
title: "Porady: ładowanie i zwalnianie zestawów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="55377-102">Porady: ładowanie i zwalnianie zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55377-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="55377-103">Zestawy odwołuje się program automatycznie zostaną załadowane w czasie kompilacji, ale jest również możliwe ładowanie określonych zestawów do bieżącej domeny aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="55377-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="55377-104">Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="55377-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="55377-105">Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces.</span><span class="sxs-lookup"><span data-stu-id="55377-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="55377-106">Nawet wtedy, gdy zestaw wykracza poza zakres, plik zestawu rzeczywiste pozostanie załadować dopóki wszystkie domeny aplikacji, które zawierałoby proces są usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="55377-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="55377-107">Aby zwolnić niektóre zestawy, a innych nie, należy rozważyć tworzenia nowej domeny aplikacji, wykonywanie kodu w tej domenie i następnie zwalnianie tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55377-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="55377-108">Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="55377-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="55377-109">Aby załadować zestawu do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55377-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="55377-110">Użyj załadować jedną z kilku metod zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="55377-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="55377-111">Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="55377-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="55377-112">Aby zwolnić domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55377-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="55377-113">Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces.</span><span class="sxs-lookup"><span data-stu-id="55377-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="55377-114">Użyj `Unload` metody z <xref:System.AppDomain> można zwolnić domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55377-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="55377-115">Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="55377-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55377-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55377-116">See Also</span></span>  
 [<span data-ttu-id="55377-117">Koncepcje programowania</span><span class="sxs-lookup"><span data-stu-id="55377-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="55377-118">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55377-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="55377-119">Porady: ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55377-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
