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
ms.openlocfilehash: 2713011d61b41dfa4d72a635c656c0c00cb42f8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643614"
---
# <a name="creating-assemblies"></a><span data-ttu-id="7a9a0-102">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="7a9a0-102">Creating Assemblies</span></span>

<span data-ttu-id="7a9a0-103">Można utworzyć pojedynczy plik lub wieloplikowe zestawy w środowisku IDE, takie jak Visual Studio lub z kompilatorów i narzędzi dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a9a0-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="7a9a0-104">Najprostsza zestaw jest pojedynczy plik o nazwie prostego, który jest ładowany do domeny pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="7a9a0-105">Ten zestaw nie może być przywoływany przez inne zestawy poza katalogiem aplikacji i nie podlegają kontroli wersji.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="7a9a0-106">Aby odinstalować aplikację składają się z zestawu, po prostu usunąć katalogu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="7a9a0-107">W przypadku wielu programistów zestawu za pomocą tych funkcji jest wszystko, co jest potrzebne do wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="7a9a0-108">Możesz utworzyć zestaw wieloplikowy z kilku modułów kodu i pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="7a9a0-109">Można również utworzyć zestaw, który może być współużytkowany przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="7a9a0-110">Zestaw współużytkowany musi mieć silną nazwę i można je wdrożyć w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="7a9a0-111">Istnieje kilka opcji, gdy grupowanie modułów kodu i zasoby do zestawów, w zależności od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="7a9a0-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

-   <span data-ttu-id="7a9a0-112">Obsługa wersji</span><span class="sxs-lookup"><span data-stu-id="7a9a0-112">Versioning</span></span>

     <span data-ttu-id="7a9a0-113">Moduły grupy, które powinny mieć te same informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-113">Group modules that should have the same version information.</span></span>

-   <span data-ttu-id="7a9a0-114">wdrażania</span><span class="sxs-lookup"><span data-stu-id="7a9a0-114">Deployment</span></span>

     <span data-ttu-id="7a9a0-115">Moduły kodu grupy i zasobów, które obsługują model wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-115">Group code modules and resources that support your model of deployment.</span></span>

-   <span data-ttu-id="7a9a0-116">Ponowne użycie</span><span class="sxs-lookup"><span data-stu-id="7a9a0-116">Reuse</span></span>

     <span data-ttu-id="7a9a0-117">Grupy modułów, jeśli one logicznie można ze sobą w celu niektóre.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="7a9a0-118">Na przykład zestaw składający się z typów i klas, rzadko używane dla programu obsługi można umieścić w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="7a9a0-119">Ponadto typy, które ma być współużytkowany z wieloma aplikacjami powinny zostać utworzone do zestawu i zestawu powinna być podpisany silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

-   <span data-ttu-id="7a9a0-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7a9a0-120">Security</span></span>

     <span data-ttu-id="7a9a0-121">Grupy modułów zawierających typy, które wymagają tych samych uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-121">Group modules containing types that require the same security permissions.</span></span>

-   <span data-ttu-id="7a9a0-122">Wyznaczanie zakresu</span><span class="sxs-lookup"><span data-stu-id="7a9a0-122">Scoping</span></span>

     <span data-ttu-id="7a9a0-123">Grupy modułów zawierających typy, których widoczność powinno zostać ograniczone do tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="7a9a0-124">Podczas udostępniania języka wspólnego zestawów środowiska uruchomieniowego do niezarządzanych aplikacji modelu COM, można wprowadzać uwagi.</span><span class="sxs-lookup"><span data-stu-id="7a9a0-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="7a9a0-125">Aby uzyskać więcej informacji na temat pracy z kodem niezarządzanym, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="7a9a0-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a9a0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a9a0-126">See also</span></span>

- [<span data-ttu-id="7a9a0-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="7a9a0-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="7a9a0-128">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="7a9a0-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="7a9a0-129">Instrukcje: Kompilacja zestawów pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="7a9a0-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="7a9a0-130">Instrukcje: Kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="7a9a0-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="7a9a0-131">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7a9a0-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7a9a0-132">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="7a9a0-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)