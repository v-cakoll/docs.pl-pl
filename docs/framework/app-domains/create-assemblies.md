---
title: "Tworzenie zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5aa4b8fa5422ae126a6027c5fe3358925873782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-assemblies"></a><span data-ttu-id="34094-102">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="34094-102">Creating Assemblies</span></span>
<span data-ttu-id="34094-103">Możesz utworzyć zestawy jednoplikowe lub wiele plików przy użyciu IDE, takich jak [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], lub kompilatory i narzędzi dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34094-103">You can create single-file or multifile assemblies using an IDE, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="34094-104">Najprostsza zestaw jest pojedynczy plik ma prostą nazwą, który jest ładowany do domeny pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34094-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="34094-105">Ten zestaw nie może odwoływać się do innych zestawów znajdujących się poza katalogiem aplikacji i nie podlegają kontroli wersji.</span><span class="sxs-lookup"><span data-stu-id="34094-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="34094-106">Aby odinstalować aplikację, składa się z zestawu, po prostu Usuń katalog, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="34094-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="34094-107">W przypadku wielu deweloperów zestawu z tych funkcji jest wszystkie, który jest wymagany do wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34094-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>  
  
 <span data-ttu-id="34094-108">Można utworzyć zestawu wieloplikowego z wielu modułów kodu i pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="34094-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="34094-109">Istnieje również możliwość utworzenia zestawu, który może być współużytkowane przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34094-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="34094-110">Zestaw udostępnionego musi mieć silnej nazwy i może zostać wdrożony w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="34094-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="34094-111">Istnieje kilka opcji, jeśli grupowanie moduły kodu i zasobów w zestawy, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="34094-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>  
  
-   <span data-ttu-id="34094-112">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="34094-112">Versioning</span></span>  
  
     <span data-ttu-id="34094-113">Moduły grupy, które powinny mieć tego samego informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="34094-113">Group modules that should have the same version information.</span></span>  
  
-   <span data-ttu-id="34094-114">wdrażania</span><span class="sxs-lookup"><span data-stu-id="34094-114">Deployment</span></span>  
  
     <span data-ttu-id="34094-115">Moduły kodu grupy i zasobów, które obsługują modelu wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="34094-115">Group code modules and resources that support your model of deployment.</span></span>  
  
-   <span data-ttu-id="34094-116">Ponowne użycie</span><span class="sxs-lookup"><span data-stu-id="34094-116">Reuse</span></span>  
  
     <span data-ttu-id="34094-117">Grupy modułów, jeśli logicznie użyciem ze sobą w celu niektóre.</span><span class="sxs-lookup"><span data-stu-id="34094-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="34094-118">Zestaw typów i klasy rzadko używane do obsługi programu można na przykład umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="34094-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="34094-119">Ponadto typy, które mają być udostępniane wielu aplikacji powinny zostać utworzone w zestawie i zestaw powinny być podpisane przy użyciu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="34094-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>  
  
-   <span data-ttu-id="34094-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="34094-120">Security</span></span>  
  
     <span data-ttu-id="34094-121">Grupa modułów zawierających typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34094-121">Group modules containing types that require the same security permissions.</span></span>  
  
-   <span data-ttu-id="34094-122">Określanie zakresu</span><span class="sxs-lookup"><span data-stu-id="34094-122">Scoping</span></span>  
  
     <span data-ttu-id="34094-123">Grupa modułów zawierających typy, których widoczność powinna być ograniczona do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="34094-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>  
  
 <span data-ttu-id="34094-124">Podczas udostępniania języka wspólnego zestawy środowiska wykonawczego niezarządzanych aplikacji modelu COM, muszą być wprowadzane uwagi.</span><span class="sxs-lookup"><span data-stu-id="34094-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="34094-125">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="34094-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34094-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34094-126">See Also</span></span>  
 [<span data-ttu-id="34094-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="34094-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="34094-128">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="34094-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="34094-129">Porady: tworzenie zestawów pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="34094-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [<span data-ttu-id="34094-130">Porady: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="34094-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="34094-131">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="34094-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="34094-132">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="34094-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
