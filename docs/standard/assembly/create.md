---
title: Tworzenie zestawów
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740510"
---
# <a name="create-assemblies"></a><span data-ttu-id="00cbb-102">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="00cbb-102">Create assemblies</span></span>

<span data-ttu-id="00cbb-103">Można tworzyć zestawy jednoplikowe lub wieloplikowe przy użyciu ide, takich jak Visual Studio lub kompilatorów i narzędzi dostarczonych przez zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="00cbb-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="00cbb-104">Najprostszy zestaw jest pojedynczy plik, który ma prostą nazwę i jest ładowany do jednej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00cbb-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="00cbb-105">Do tego zestawu nie mogą odwoływać się inne zestawy poza katalogiem aplikacji i nie są poddawane sprawdzaniu wersji.</span><span class="sxs-lookup"><span data-stu-id="00cbb-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="00cbb-106">Aby odinstalować aplikację składającą się z zestawu, wystarczy usunąć katalog, w którym się znajduje.</span><span class="sxs-lookup"><span data-stu-id="00cbb-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="00cbb-107">Dla wielu deweloperów zestaw z tymi funkcjami jest wszystko, co jest potrzebne do wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00cbb-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="00cbb-108">Można utworzyć zestaw wieloplikowy z kilku modułów kodu i plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="00cbb-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="00cbb-109">Można również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00cbb-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="00cbb-110">Zestaw udostępniony musi mieć silną nazwę i może być wdrożony w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="00cbb-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="00cbb-111">Podczas grupowania modułów kodu i zasobów w zestawy dostępnych jest kilka opcji, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="00cbb-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="00cbb-112">Obsługa wersji</span><span class="sxs-lookup"><span data-stu-id="00cbb-112">Versioning</span></span>

     <span data-ttu-id="00cbb-113">Grupuj moduły, które powinny mieć te same informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="00cbb-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="00cbb-114">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="00cbb-114">Deployment</span></span>

     <span data-ttu-id="00cbb-115">Grupuj moduły kodu i zasoby, które obsługują model wdrażania.</span><span class="sxs-lookup"><span data-stu-id="00cbb-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="00cbb-116">Ponowne użycie</span><span class="sxs-lookup"><span data-stu-id="00cbb-116">Reuse</span></span>

     <span data-ttu-id="00cbb-117">Grupuj moduły, jeśli mogą być logicznie używane razem do pewnego celu.</span><span class="sxs-lookup"><span data-stu-id="00cbb-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="00cbb-118">Na przykład zestaw składający się z typów i klas rzadko używanych do konserwacji programu można umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="00cbb-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="00cbb-119">Ponadto typy, które mają być udostępniane z wieloma aplikacjami powinny być pogrupowane w zestaw i zestaw powinien być podpisany o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="00cbb-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="00cbb-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="00cbb-120">Security</span></span>

     <span data-ttu-id="00cbb-121">Grupuj moduły zawierające typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="00cbb-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="00cbb-122">Zakresu</span><span class="sxs-lookup"><span data-stu-id="00cbb-122">Scoping</span></span>

     <span data-ttu-id="00cbb-123">Grupuj moduły zawierające typy, których widoczność powinna być ograniczona do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="00cbb-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="00cbb-124">Istnieją szczególne zagadnienia podczas udostępniania zestawów w czasie wykonywania języka wspólnego dla niezarządzanych aplikacji COM.</span><span class="sxs-lookup"><span data-stu-id="00cbb-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="00cbb-125">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [Udostępnianie składników .NET Framework do com](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="00cbb-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00cbb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00cbb-126">See also</span></span>

- [<span data-ttu-id="00cbb-127">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="00cbb-127">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="00cbb-128">Jak: Tworzenie zestawu pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="00cbb-128">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="00cbb-129">Jak: Tworzenie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="00cbb-129">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="00cbb-130">Jak program runtime lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="00cbb-130">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="00cbb-131">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="00cbb-131">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
