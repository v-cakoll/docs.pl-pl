---
title: Tworzenie zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314a94be140b392964951299fba2fed4ac7e6e68
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566792"
---
# <a name="creating-assemblies"></a><span data-ttu-id="d853c-102">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="d853c-102">Creating Assemblies</span></span>

<span data-ttu-id="d853c-103">Można tworzyć zestawy Jednoplikowe lub wieloplikowe za pomocą IDE, takie jak Visual Studio, lub kompilatory i narzędzia dostarczone przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="d853c-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="d853c-104">Najprostszym zestawem jest pojedynczy plik, który ma prostą nazwę i jest ładowany do pojedynczej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d853c-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="d853c-105">Ten zestaw nie może odwoływać się do innych zestawów poza katalogiem aplikacji i nie jest sprawdzany Sprawdzanie wersji.</span><span class="sxs-lookup"><span data-stu-id="d853c-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="d853c-106">Aby odinstalować aplikację utworzoną z zestawu, wystarczy usunąć znajdujący się w niej katalog.</span><span class="sxs-lookup"><span data-stu-id="d853c-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="d853c-107">W przypadku wielu deweloperów zestaw z tymi funkcjami jest wymagany do wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d853c-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="d853c-108">Zestaw wieloplikowy można utworzyć z kilku modułów kodu i plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="d853c-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="d853c-109">Możesz również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d853c-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="d853c-110">Zestaw współużytkowany musi mieć silną nazwę i można go wdrożyć w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="d853c-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="d853c-111">Istnieje kilka opcji grupowania modułów kodu i zasobów w zestawy, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="d853c-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="d853c-112">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="d853c-112">Versioning</span></span>

     <span data-ttu-id="d853c-113">Grupuj moduły, które powinny mieć te same informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="d853c-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="d853c-114">wdrażania</span><span class="sxs-lookup"><span data-stu-id="d853c-114">Deployment</span></span>

     <span data-ttu-id="d853c-115">Grupuj moduły kodu i zasoby, które obsługują model wdrażania.</span><span class="sxs-lookup"><span data-stu-id="d853c-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="d853c-116">Było</span><span class="sxs-lookup"><span data-stu-id="d853c-116">Reuse</span></span>

     <span data-ttu-id="d853c-117">Grupuj moduły, jeśli mogą być logicznie używane razem do pewnego celu.</span><span class="sxs-lookup"><span data-stu-id="d853c-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="d853c-118">Na przykład zestaw składający się z typów i klas używanych rzadko do konserwacji programu można umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d853c-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="d853c-119">Ponadto typy, które mają być współużytkowane z wieloma aplikacjami, powinny być pogrupowane w zestaw, a zestaw powinien być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d853c-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="d853c-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d853c-120">Security</span></span>

     <span data-ttu-id="d853c-121">Moduły grupy zawierające typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d853c-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="d853c-122">Zakresów</span><span class="sxs-lookup"><span data-stu-id="d853c-122">Scoping</span></span>

     <span data-ttu-id="d853c-123">Moduły grupy zawierające typy, których widoczność powinna być ograniczona do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d853c-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="d853c-124">Przed udostępnieniem zestawów środowiska uruchomieniowego języka wspólnego dla niezarządzanych aplikacji COM należy uwzględnić specjalne zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="d853c-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="d853c-125">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [Udostępnianie składników .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="d853c-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d853c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d853c-126">See also</span></span>

- [<span data-ttu-id="d853c-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d853c-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="d853c-128">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="d853c-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="d853c-129">Instrukcje: Kompilowanie zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="d853c-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="d853c-130">Instrukcje: Kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="d853c-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="d853c-131">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d853c-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d853c-132">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="d853c-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
