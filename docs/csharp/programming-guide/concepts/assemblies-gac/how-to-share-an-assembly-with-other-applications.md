---
title: 'Porady: dzielenie się zestawem z innymi aplikacjami (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: beadd6adb176c3fd4e6dde94d95194aea790a2fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="cd815-102">Porady: dzielenie się zestawem z innymi aplikacjami (C#)</span><span class="sxs-lookup"><span data-stu-id="cd815-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="cd815-103">Zestawy mogą być prywatne lub współużytkowane: domyślnie większości programów proste składają się z zestaw prywatny, ponieważ nie są one przeznaczone do użycia przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="cd815-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="cd815-104">Aby można było dzielenie się zestawem z innymi aplikacjami, należy umieścić w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="cd815-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="cd815-105">Udostępnianie zestawów</span><span class="sxs-lookup"><span data-stu-id="cd815-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="cd815-106">Utwórz używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd815-106">Create your assembly.</span></span> <span data-ttu-id="cd815-107">Aby uzyskać więcej informacji, zobacz [tworzenie zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="cd815-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="cd815-108">Przypisz silnej nazwy do używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd815-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="cd815-109">Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="cd815-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="cd815-110">Informacje o wersji należy przypisać do używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd815-110">Assign version information to your assembly.</span></span> <span data-ttu-id="cd815-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="cd815-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="cd815-112">Dodaj użytkownika zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="cd815-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="cd815-113">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="cd815-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="cd815-114">Dostęp do tych typów zawartych w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd815-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="cd815-115">Aby uzyskać więcej informacji, zobacz [porady: odwołanie zestawu Strong-Named](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="cd815-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd815-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd815-116">See Also</span></span>  
 [<span data-ttu-id="cd815-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cd815-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd815-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="cd815-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
