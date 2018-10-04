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
ms.openlocfilehash: df8590b38ace0abcc370f94852a35569b95c4a2d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582453"
---
# <a name="creating-assemblies"></a><span data-ttu-id="70a4e-102">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="70a4e-102">Creating Assemblies</span></span>

<span data-ttu-id="70a4e-103">Można utworzyć pojedynczy plik lub wieloplikowe zestawy w środowisku IDE, takie jak Visual Studio lub z kompilatorów i narzędzi dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70a4e-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="70a4e-104">Najprostsza zestaw jest pojedynczy plik o nazwie prostego, który jest ładowany do domeny pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70a4e-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="70a4e-105">Ten zestaw nie może być przywoływany przez inne zestawy poza katalogiem aplikacji i nie podlegają kontroli wersji.</span><span class="sxs-lookup"><span data-stu-id="70a4e-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="70a4e-106">Aby odinstalować aplikację składają się z zestawu, po prostu usunąć katalogu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="70a4e-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="70a4e-107">W przypadku wielu programistów zestawu za pomocą tych funkcji jest wszystko, co jest potrzebne do wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70a4e-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="70a4e-108">Możesz utworzyć zestaw wieloplikowy z kilku modułów kodu i pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="70a4e-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="70a4e-109">Można również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70a4e-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="70a4e-110">Zestaw współużytkowany musi mieć silną nazwę i można je wdrożyć w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="70a4e-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="70a4e-111">Istnieje kilka opcji, gdy grupowanie modułów kodu i zasoby do zestawów, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="70a4e-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

-   <span data-ttu-id="70a4e-112">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="70a4e-112">Versioning</span></span>

     <span data-ttu-id="70a4e-113">Moduły grupy, które powinny mieć te same informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="70a4e-113">Group modules that should have the same version information.</span></span>

-   <span data-ttu-id="70a4e-114">wdrażania</span><span class="sxs-lookup"><span data-stu-id="70a4e-114">Deployment</span></span>

     <span data-ttu-id="70a4e-115">Moduły kodu grupy i zasobów, które obsługują model wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="70a4e-115">Group code modules and resources that support your model of deployment.</span></span>

-   <span data-ttu-id="70a4e-116">Ponowne użycie</span><span class="sxs-lookup"><span data-stu-id="70a4e-116">Reuse</span></span>

     <span data-ttu-id="70a4e-117">Grupy modułów, jeśli one logicznie można ze sobą w celu niektóre.</span><span class="sxs-lookup"><span data-stu-id="70a4e-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="70a4e-118">Na przykład zestaw składający się z typów i klas, rzadko używane dla programu obsługi można umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="70a4e-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="70a4e-119">Ponadto typy, które ma być współużytkowany z wieloma aplikacjami powinny zostać utworzone do zestawu i zestawu powinna być podpisany silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="70a4e-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

-   <span data-ttu-id="70a4e-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="70a4e-120">Security</span></span>

     <span data-ttu-id="70a4e-121">Grupy modułów zawierających typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="70a4e-121">Group modules containing types that require the same security permissions.</span></span>

-   <span data-ttu-id="70a4e-122">Wyznaczanie zakresu</span><span class="sxs-lookup"><span data-stu-id="70a4e-122">Scoping</span></span>

     <span data-ttu-id="70a4e-123">Grupy modułów zawierających typy, których widoczność powinno zostać ograniczone do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="70a4e-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="70a4e-124">Podczas udostępniania języka wspólnego zestawów środowiska uruchomieniowego do niezarządzanych aplikacji modelu COM, można wprowadzać uwagi.</span><span class="sxs-lookup"><span data-stu-id="70a4e-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="70a4e-125">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="70a4e-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70a4e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70a4e-126">See Also</span></span>

- [<span data-ttu-id="70a4e-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="70a4e-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="70a4e-128">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="70a4e-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="70a4e-129">Instrukcje: kompilacja zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="70a4e-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="70a4e-130">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="70a4e-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="70a4e-131">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="70a4e-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="70a4e-132">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="70a4e-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)