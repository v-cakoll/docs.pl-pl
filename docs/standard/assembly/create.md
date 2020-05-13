---
title: Tworzenie zestawów
description: Dowiedz się więcej na temat tworzenia zestawów jednoplikowych lub wieloplikowych przy użyciu środowiska IDE, takiego jak Visual Studio, lub kompilatorów i narzędzi dostarczanych przez Windows SDK.
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 3e17d6a066d937a161135b8b03c3f9258f3586b0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378511"
---
# <a name="create-assemblies"></a><span data-ttu-id="577cf-103">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="577cf-103">Create assemblies</span></span>

<span data-ttu-id="577cf-104">Można tworzyć zestawy Jednoplikowe lub wieloplikowe za pomocą IDE, takie jak Visual Studio, lub kompilatory i narzędzia dostarczone przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="577cf-104">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="577cf-105">Najprostszym zestawem jest pojedynczy plik, który ma prostą nazwę i jest ładowany do pojedynczej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="577cf-105">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="577cf-106">Ten zestaw nie może odwoływać się do innych zestawów poza katalogiem aplikacji i nie jest sprawdzany Sprawdzanie wersji.</span><span class="sxs-lookup"><span data-stu-id="577cf-106">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="577cf-107">Aby odinstalować aplikację utworzoną z zestawu, wystarczy usunąć znajdujący się w niej katalog.</span><span class="sxs-lookup"><span data-stu-id="577cf-107">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="577cf-108">W przypadku wielu deweloperów zestaw z tymi funkcjami jest wymagany do wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="577cf-108">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="577cf-109">Zestaw wieloplikowy można utworzyć z kilku modułów kodu i plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="577cf-109">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="577cf-110">Możesz również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="577cf-110">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="577cf-111">Zestaw współużytkowany musi mieć silną nazwę i można go wdrożyć w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="577cf-111">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="577cf-112">Istnieje kilka opcji grupowania modułów kodu i zasobów w zestawy, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="577cf-112">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="577cf-113">Obsługa wersji</span><span class="sxs-lookup"><span data-stu-id="577cf-113">Versioning</span></span>

     <span data-ttu-id="577cf-114">Grupuj moduły, które powinny mieć te same informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="577cf-114">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="577cf-115">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="577cf-115">Deployment</span></span>

     <span data-ttu-id="577cf-116">Grupuj moduły kodu i zasoby, które obsługują model wdrażania.</span><span class="sxs-lookup"><span data-stu-id="577cf-116">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="577cf-117">Ponowne użycie</span><span class="sxs-lookup"><span data-stu-id="577cf-117">Reuse</span></span>

     <span data-ttu-id="577cf-118">Grupuj moduły, jeśli mogą być logicznie używane razem do pewnego celu.</span><span class="sxs-lookup"><span data-stu-id="577cf-118">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="577cf-119">Na przykład zestaw składający się z typów i klas używanych rzadko do konserwacji programu można umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="577cf-119">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="577cf-120">Ponadto typy, które mają być współużytkowane z wieloma aplikacjami, powinny być pogrupowane w zestaw, a zestaw powinien być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="577cf-120">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="577cf-121">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="577cf-121">Security</span></span>

     <span data-ttu-id="577cf-122">Moduły grupy zawierające typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="577cf-122">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="577cf-123">Zakresów</span><span class="sxs-lookup"><span data-stu-id="577cf-123">Scoping</span></span>

     <span data-ttu-id="577cf-124">Moduły grupy zawierające typy, których widoczność powinna być ograniczona do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="577cf-124">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="577cf-125">Istnieją specjalne zagadnienia dotyczące tworzenia zestawów środowiska uruchomieniowego języka wspólnego dla niezarządzanych aplikacji COM.</span><span class="sxs-lookup"><span data-stu-id="577cf-125">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="577cf-126">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie .NET Framework składników do modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="577cf-126">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="577cf-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="577cf-127">See also</span></span>

- [<span data-ttu-id="577cf-128">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="577cf-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="577cf-129">Instrukcje: tworzenie zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="577cf-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="577cf-130">Instrukcje: tworzenie zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="577cf-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="577cf-131">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="577cf-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="577cf-132">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="577cf-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
