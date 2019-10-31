---
title: Tworzenie zestawów
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 8a00784e6aa2d663c738339367b4076e79ed9c95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122499"
---
# <a name="create-assemblies"></a><span data-ttu-id="5f145-102">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="5f145-102">Create assemblies</span></span>

<span data-ttu-id="5f145-103">Można tworzyć zestawy Jednoplikowe lub wieloplikowe za pomocą IDE, takie jak Visual Studio, lub kompilatory i narzędzia dostarczone przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="5f145-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="5f145-104">Najprostszym zestawem jest pojedynczy plik, który ma prostą nazwę i jest ładowany do pojedynczej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f145-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="5f145-105">Ten zestaw nie może odwoływać się do innych zestawów poza katalogiem aplikacji i nie jest sprawdzany Sprawdzanie wersji.</span><span class="sxs-lookup"><span data-stu-id="5f145-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="5f145-106">Aby odinstalować aplikację utworzoną z zestawu, wystarczy usunąć znajdujący się w niej katalog.</span><span class="sxs-lookup"><span data-stu-id="5f145-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="5f145-107">W przypadku wielu deweloperów zestaw z tymi funkcjami jest wymagany do wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f145-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="5f145-108">Zestaw wieloplikowy można utworzyć z kilku modułów kodu i plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="5f145-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="5f145-109">Możesz również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f145-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="5f145-110">Zestaw współużytkowany musi mieć silną nazwę i można go wdrożyć w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5f145-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="5f145-111">Istnieje kilka opcji grupowania modułów kodu i zasobów w zestawy, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="5f145-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="5f145-112">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="5f145-112">Versioning</span></span>

     <span data-ttu-id="5f145-113">Grupuj moduły, które powinny mieć te same informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="5f145-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="5f145-114">wdrażania</span><span class="sxs-lookup"><span data-stu-id="5f145-114">Deployment</span></span>

     <span data-ttu-id="5f145-115">Grupuj moduły kodu i zasoby, które obsługują model wdrażania.</span><span class="sxs-lookup"><span data-stu-id="5f145-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="5f145-116">Było</span><span class="sxs-lookup"><span data-stu-id="5f145-116">Reuse</span></span>

     <span data-ttu-id="5f145-117">Grupuj moduły, jeśli mogą być logicznie używane razem do pewnego celu.</span><span class="sxs-lookup"><span data-stu-id="5f145-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="5f145-118">Na przykład zestaw składający się z typów i klas używanych rzadko do konserwacji programu można umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="5f145-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="5f145-119">Ponadto typy, które mają być współużytkowane z wieloma aplikacjami, powinny być pogrupowane w zestaw, a zestaw powinien być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5f145-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="5f145-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5f145-120">Security</span></span>

     <span data-ttu-id="5f145-121">Moduły grupy zawierające typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5f145-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="5f145-122">Zakresów</span><span class="sxs-lookup"><span data-stu-id="5f145-122">Scoping</span></span>

     <span data-ttu-id="5f145-123">Moduły grupy zawierające typy, których widoczność powinna być ograniczona do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5f145-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="5f145-124">Istnieją specjalne zagadnienia dotyczące tworzenia zestawów środowiska uruchomieniowego języka wspólnego dla niezarządzanych aplikacji COM.</span><span class="sxs-lookup"><span data-stu-id="5f145-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="5f145-125">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie .NET Framework składników do modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="5f145-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f145-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f145-126">See also</span></span>

- [<span data-ttu-id="5f145-127">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="5f145-127">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="5f145-128">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="5f145-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="5f145-129">Instrukcje: kompilowanie zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="5f145-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="5f145-130">Instrukcje: kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="5f145-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="5f145-131">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="5f145-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="5f145-132">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="5f145-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
