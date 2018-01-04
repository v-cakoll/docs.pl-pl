---
title: "Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c914b566727d882939c23a982fad5db12985de5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a><span data-ttu-id="fac24-102">Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego</span><span class="sxs-lookup"><span data-stu-id="fac24-102">Guidelines for Creating Components for Side-by-Side Execution</span></span>
<span data-ttu-id="fac24-103">Wykonaj te ogólne wytyczne, aby utworzyć aplikacje zarządzane lub składniki przeznaczone do wykonywania side-by-side:</span><span class="sxs-lookup"><span data-stu-id="fac24-103">Follow these general guidelines to create managed applications or components designed for side-by-side execution:</span></span>  
  
-   <span data-ttu-id="fac24-104">Typ tożsamości należy powiązać określonej wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="fac24-104">Bind type identity to a particular version of a file.</span></span>  
  
     <span data-ttu-id="fac24-105">Środowisko uruchomieniowe języka wspólnego wiąże tożsamość typu wersja określonego pliku przy użyciu zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="fac24-105">The common language runtime binds type identity to a particular file version by using strong-named assemblies.</span></span> <span data-ttu-id="fac24-106">Aby utworzyć aplikację lub składnik do wykonania side-by-side, należy podać wszystkie zestawy silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fac24-106">To create an application or component for side-by-side execution, you must give all assemblies a strong name.</span></span> <span data-ttu-id="fac24-107">Tworzy tożsamość dokładny typ oraz zapewnia, że wszelkie rozpoznawania typu jest kierowane do poprawnego pliku.</span><span class="sxs-lookup"><span data-stu-id="fac24-107">This creates precise type identity and ensures that any type resolution is directed to the correct file.</span></span> <span data-ttu-id="fac24-108">Zestaw o silnej nazwie zawiera wersję, kulturę i informacje o wydawcy używający środowiska uruchomieniowego można znaleźć poprawnego pliku do spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="fac24-108">A strong-named assembly contains version, culture, and publisher information that the runtime uses to locate the correct file to fulfill a binding request.</span></span>  
  
-   <span data-ttu-id="fac24-109">Użyj obsługujący wersji magazynu.</span><span class="sxs-lookup"><span data-stu-id="fac24-109">Use version-aware storage.</span></span>  
  
     <span data-ttu-id="fac24-110">Środowisko uruchomieniowe używa globalnej pamięci podręcznej zestawów, aby zapewnić obsługujący wersji magazynu.</span><span class="sxs-lookup"><span data-stu-id="fac24-110">The runtime uses the global assembly cache to provide version-aware storage.</span></span> <span data-ttu-id="fac24-111">Globalna pamięć podręczna zestawów to struktura obsługująca wersji katalogu zainstalowane na każdym komputerze, który używa programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fac24-111">The global assembly cache is a version-aware directory structure installed on every computer that uses the .NET Framework.</span></span> <span data-ttu-id="fac24-112">Zestawy zainstalowany w globalnej pamięci podręcznej zestawów nie zostaną zastąpione po zainstalowaniu nowej wersji tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fac24-112">Assemblies installed in the global assembly cache are not overwritten when a new version of that assembly is installed.</span></span>  
  
-   <span data-ttu-id="fac24-113">Utwórz aplikację lub składnik, który jest uruchamiany w izolacji.</span><span class="sxs-lookup"><span data-stu-id="fac24-113">Create an application or component that runs in isolation.</span></span>  
  
     <span data-ttu-id="fac24-114">Aplikacja lub składnik, który jest uruchamiany w izolacji muszą zarządzać zasobów, aby uniknąć konfliktów, jeśli dwa wystąpienia aplikacji lub składnika jest uruchomionych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fac24-114">An application or component that runs in isolation must manage resources to avoid conflicts when two instances of the application or component are running simultaneously.</span></span> <span data-ttu-id="fac24-115">Aplikacja lub składnik również użyć struktury określonej wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="fac24-115">The application or component must also use a version-specific file structure.</span></span>  
  
## <a name="application-and-component-isolation"></a><span data-ttu-id="fac24-116">Aplikacji i izolacji składnika</span><span class="sxs-lookup"><span data-stu-id="fac24-116">Application and Component Isolation</span></span>  
 <span data-ttu-id="fac24-117">Jeden klucz pomyślnie projektowania aplikacji lub składnika w celu wykonywania side-by-side jest izolacji.</span><span class="sxs-lookup"><span data-stu-id="fac24-117">One key to successfully designing an application or component for side-by-side execution is isolation.</span></span> <span data-ttu-id="fac24-118">Aplikacja lub składnik musi zarządzać wszystkie zasoby, we/wy, szczególnie dla plików w sposób izolowany.</span><span class="sxs-lookup"><span data-stu-id="fac24-118">The application or component must manage all resources, particularly file I/O, in an isolated manner.</span></span> <span data-ttu-id="fac24-119">Skorzystaj z następujących wskazówek, aby upewnić się, że aplikacja lub składnik jest uruchamiany w izolacji:</span><span class="sxs-lookup"><span data-stu-id="fac24-119">Follow these guidelines to make sure your application or component runs in isolation:</span></span>  
  
-   <span data-ttu-id="fac24-120">Zapisywanie w rejestrze w sposób określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="fac24-120">Write to the registry in a version-specific way.</span></span> <span data-ttu-id="fac24-121">Przechowywanie wartości w gałęzi lub klucze, które wskazują wersji i nie udostępniaj informacje lub stan między wersjami składnika.</span><span class="sxs-lookup"><span data-stu-id="fac24-121">Store values in hives or keys that indicate the version, and do not share information or state across versions of a component.</span></span> <span data-ttu-id="fac24-122">Zapobiega to dwie aplikacje lub składniki działające w tym samym czasie zastępowaniu informacji.</span><span class="sxs-lookup"><span data-stu-id="fac24-122">This prevents two applications or components running at the same time from overwriting information.</span></span>  
  
-   <span data-ttu-id="fac24-123">Wprowadź obiektów o nazwie jądra określonej wersji, tak aby nie występuje sytuacja wyścigu.</span><span class="sxs-lookup"><span data-stu-id="fac24-123">Make named kernel objects version-specific so that a race condition does not occur.</span></span> <span data-ttu-id="fac24-124">Na przykład sytuacja wyścigu występuje, gdy dwie semaforów z dwie wersje tej samej aplikacji, poczekaj na siebie.</span><span class="sxs-lookup"><span data-stu-id="fac24-124">For example, a race condition occurs when two semaphores from two versions of the same application wait on each other.</span></span>  
  
-   <span data-ttu-id="fac24-125">Należy obsługujący wersji nazw plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="fac24-125">Make file and directory names version-aware.</span></span> <span data-ttu-id="fac24-126">Oznacza to, że plik struktury polegać na informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="fac24-126">This means that file structures should rely on version information.</span></span>  
  
-   <span data-ttu-id="fac24-127">Utworzenie kont użytkowników i grup w sposób określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="fac24-127">Create user accounts and groups in a version-specific manner.</span></span> <span data-ttu-id="fac24-128">Konta użytkowników i grup utworzonych przez aplikację powinny zostać zidentyfikowane na podstawie wersji.</span><span class="sxs-lookup"><span data-stu-id="fac24-128">User accounts and groups created by an application should be identified by version.</span></span> <span data-ttu-id="fac24-129">Nie udostępniaj kont użytkowników i grup między wersjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fac24-129">Do not share user accounts and groups between versions of an application.</span></span>  
  
## <a name="installing-and-uninstalling-versions"></a><span data-ttu-id="fac24-130">Instalowanie i odinstalowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="fac24-130">Installing and Uninstalling Versions</span></span>  
 <span data-ttu-id="fac24-131">Podczas projektowania aplikacji do wykonania side-by-side, skorzystaj z następujących wskazówek dotyczących instalowania i odinstalowywania wersji:</span><span class="sxs-lookup"><span data-stu-id="fac24-131">When designing an application for side-by-side execution, follow these guidelines concerning installing and uninstalling versions:</span></span>  
  
-   <span data-ttu-id="fac24-132">Nie należy usuwać informacji z rejestru, który może być wymagany przez inne aplikacje uruchomione w innej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fac24-132">Do not delete information from the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="fac24-133">Nie zastępuj informacje w rejestrze, który może być wymagany przez inne aplikacje uruchomione w innej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fac24-133">Do not replace information in the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="fac24-134">Nie wyrejestrować składników COM, które mogą być wymagane przez inne aplikacje uruchomione w innej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fac24-134">Do not unregister COM components that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="fac24-135">Nie zmieniaj **InprocServer32** lub inne wpisy rejestru dotyczące serwera COM, który został już zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="fac24-135">Do not change **InprocServer32** or other registry entries for a COM server that was already registered.</span></span>  
  
-   <span data-ttu-id="fac24-136">Nie należy usuwać konta użytkowników lub grupy, które mogą być wymagane przez inne aplikacje uruchomione w innej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fac24-136">Do not delete user accounts or groups that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="fac24-137">Nie dodawaj żadnych czynności w rejestrze, który zawiera ścieżkę wycofanie.</span><span class="sxs-lookup"><span data-stu-id="fac24-137">Do not add anything to the registry that contains an unversioned path.</span></span>  
  
## <a name="file-version-number-and-assembly-version-number"></a><span data-ttu-id="fac24-138">Numer wersji pliku i numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="fac24-138">File Version Number and Assembly Version Number</span></span>  
 <span data-ttu-id="fac24-139">Wersja pliku jest zasób wersji Win32, który nie jest używany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fac24-139">File version is a Win32 version resource that is not used by the runtime.</span></span> <span data-ttu-id="fac24-140">Ogólnie rzecz biorąc należy zaktualizować wersję pliku, nawet w przypadku aktualizacji w miejscu.</span><span class="sxs-lookup"><span data-stu-id="fac24-140">In general, you update the file version even for an in-place update.</span></span> <span data-ttu-id="fac24-141">Dwie identyczne pliki mogą mieć inny plik informacji o wersji, a dwóch różnych plików mogą mieć tej samej informacji o wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="fac24-141">Two identical files can have different file version information, and two different files can have the same file version information.</span></span>  
  
 <span data-ttu-id="fac24-142">Wersja zestawu jest używana przez środowisko uruchomieniowe dla powiązań zestawów.</span><span class="sxs-lookup"><span data-stu-id="fac24-142">The assembly version is used by the runtime for assembly binding.</span></span> <span data-ttu-id="fac24-143">Dwa identyczne zestawy za pomocą różnych numerów wersji są traktowane jako dwa różne zestawy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fac24-143">Two identical assemblies with different version numbers are treated as two different assemblies by the runtime.</span></span>  
  
 <span data-ttu-id="fac24-144">[Narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pozwala zastąpić zestawu, gdy numer wersji pliku jest nowsza.</span><span class="sxs-lookup"><span data-stu-id="fac24-144">The [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) allows you to replace an assembly when only the file version number is newer.</span></span> <span data-ttu-id="fac24-145">Instalator zazwyczaj nie są instalowane za pośrednictwem zestawu chyba, że numer wersji zestawu jest większa.</span><span class="sxs-lookup"><span data-stu-id="fac24-145">The installer generally does not install over an assembly unless the assembly version number is greater.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac24-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fac24-146">See Also</span></span>  
 [<span data-ttu-id="fac24-147">Wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="fac24-147">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)  
 [<span data-ttu-id="fac24-148">Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="fac24-148">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
