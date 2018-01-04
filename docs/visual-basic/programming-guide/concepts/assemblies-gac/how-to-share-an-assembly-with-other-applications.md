---
title: "Porady: dzielenie się zestawem z innymi aplikacjami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c079250211a4216b09e84140ff537b3f57127967
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="dd43a-102">Porady: dzielenie się zestawem z innymi aplikacjami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd43a-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="dd43a-103">Zestawy mogą być prywatne lub współużytkowane: domyślnie większości programów proste składają się z zestaw prywatny, ponieważ nie są one przeznaczone do użycia przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="dd43a-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="dd43a-104">Aby można było dzielenie się zestawem z innymi aplikacjami, należy umieścić w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="dd43a-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="dd43a-105">Udostępnianie zestawów</span><span class="sxs-lookup"><span data-stu-id="dd43a-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="dd43a-106">Utwórz używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dd43a-106">Create your assembly.</span></span> <span data-ttu-id="dd43a-107">Aby uzyskać więcej informacji, zobacz [tworzenie zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dd43a-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="dd43a-108">Przypisz silnej nazwy do używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dd43a-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="dd43a-109">Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dd43a-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="dd43a-110">Informacje o wersji należy przypisać do używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dd43a-110">Assign version information to your assembly.</span></span> <span data-ttu-id="dd43a-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="dd43a-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="dd43a-112">Dodaj użytkownika zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="dd43a-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="dd43a-113">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="dd43a-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="dd43a-114">Dostęp do tych typów zawartych w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd43a-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="dd43a-115">Aby uzyskać więcej informacji, zobacz [porady: odwołanie zestawu Strong-Named](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="dd43a-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd43a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd43a-116">See Also</span></span>  
 <span data-ttu-id="dd43a-117">[Koncepcje programowania](../../../../visual-basic/programming-guide/concepts/index.md) [zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="dd43a-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="dd43a-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="dd43a-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
