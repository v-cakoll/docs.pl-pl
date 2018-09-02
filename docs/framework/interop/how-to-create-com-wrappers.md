---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e30b1a5a4d3b50c80edaac29cbd6b90f3ddd103b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400506"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="326ee-102">Porady: tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="326ee-102">How to: Create COM Wrappers</span></span>
<span data-ttu-id="326ee-103">Otoki Component Object Model (COM) można utworzyć za pomocą [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] funkcji lub .NET Framework narzędzia Tlbimp.exe i Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="326ee-103">You can create Component Object Model (COM) wrappers by using [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="326ee-104">Obie metody wygenerować dwa typy otok COM:</span><span class="sxs-lookup"><span data-stu-id="326ee-104">Both methods generate two types of COM wrappers:</span></span>  
  
-   <span data-ttu-id="326ee-105">A [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) z biblioteki typów, aby uruchomić obiektów COM w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="326ee-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>  
  
-   <span data-ttu-id="326ee-106">A [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md) za pomocą ustawień rejestru wymagane do uruchamiania zarządzanego obiektu w aplikacji natywnej.</span><span class="sxs-lookup"><span data-stu-id="326ee-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>  
  
 <span data-ttu-id="326ee-107">W [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], można dodać otoki COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="326ee-107">In [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can add the COM wrapper as a reference to your project.</span></span>  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a><span data-ttu-id="326ee-108">Zawijanie obiektów COM w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="326ee-108">Wrapping COM Objects in a Managed Application</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="326ee-109">Aby utworzyć wywoływana otoka środowiska uruchomieniowego przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="326ee-109">To create a runtime callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="326ee-110">Otwórz projekt dla aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="326ee-110">Open the project for your managed application.</span></span>  
  
2.  <span data-ttu-id="326ee-111">Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="326ee-111">On the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="326ee-112">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="326ee-112">On the **Project** menu, click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="326ee-113">W oknie dialogowym Dodaj odwołanie, kliknij przycisk **COM** , a następnie wybierz składnik, należy użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="326ee-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>  
  
     <span data-ttu-id="326ee-114">W **Eksploratora rozwiązań**, należy pamiętać, że składnik COM został dodany do folderu odwołań w projekcie.</span><span class="sxs-lookup"><span data-stu-id="326ee-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>  
  
 <span data-ttu-id="326ee-115">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="326ee-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="326ee-116">Możesz rozpocząć od zadeklarowania obiektu, takie jak za pomocą `Imports` poufności informacji dotyczące [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] lub `Using` poufności informacji dotyczące [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="326ee-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="326ee-117">Jeśli chcesz program Microsoft Office składniki, najpierw zainstaluj [podstawowe zestawy międzyoperacyjne pakietu Office Microsoft](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="326ee-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="326ee-118">W kroku 4, wybierz najnowszą dostępną dla produktu Office ma, takich jak biblioteki obiektów **Biblioteka obiektów programu Microsoft Word 11.0**.</span><span class="sxs-lookup"><span data-stu-id="326ee-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="326ee-119">Aby utworzyć wywoływana otoka środowiska uruchomieniowego przy użyciu narzędzi programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="326ee-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="326ee-120">Uruchom [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="326ee-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="326ee-121">To narzędzie tworzy zestaw, który zawiera metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="326ee-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a><span data-ttu-id="326ee-122">OPAKOWYWANIE zarządzane obiekty w aplikacji macierzystej</span><span class="sxs-lookup"><span data-stu-id="326ee-122">Wrapping Managed Objects in a Native Application</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="326ee-123">Aby utworzyć wywołalne opakowanie COM za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="326ee-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="326ee-124">Utwórz projekt biblioteki klas dla zarządzanej klasy, która ma zostać uruchomiony w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="326ee-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="326ee-125">Klasa musi mieć domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="326ee-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="326ee-126">Sprawdź, czy masz pełną Czteroczęściowy numer wersji zestawu w pliku AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="326ee-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="326ee-127">Ta liczba jest wymagany do obsługi przechowywania wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="326ee-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="326ee-128">Aby uzyskać więcej informacji na temat numerów wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="326ee-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="326ee-129">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="326ee-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="326ee-130">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="326ee-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="326ee-131">Wybierz **Zarejestruj dla współdziałania COM** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="326ee-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="326ee-132">Podczas kompilowania projektu zestawu jest automatycznie rejestrowane dla współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="326ee-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="326ee-133">Jeśli tworzysz aplikacji macierzystej [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], można użyć zestawu, klikając **Dodaj odwołanie** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="326ee-133">If you are building a native application in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="326ee-134">Aby utworzyć wywołalne opakowanie COM za pomocą narzędzi programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="326ee-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="326ee-135">Uruchom [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="326ee-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
 <span data-ttu-id="326ee-136">To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="326ee-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="326ee-137">W rezultacie klientów modelu COM może przezroczyste Tworzenie klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="326ee-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="326ee-138">Można użyć zestawu, tak jakby natywnych klasa COM.</span><span class="sxs-lookup"><span data-stu-id="326ee-138">You can use the assembly as if it were a native COM class.</span></span>  
  
 <span data-ttu-id="326ee-139">Uruchamianie Regasm.exe na zestawu znajdującego się w dowolnym katalogu, a następnie uruchom [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) przenieść je do globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="326ee-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="326ee-140">Przenoszenie zestawu nie unieważnia wpisy rejestru lokalizacji, ponieważ w globalnej pamięci podręcznej jest badany zawsze, jeśli zestaw nie zostanie znaleziony gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="326ee-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326ee-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="326ee-141">See Also</span></span>  
 [<span data-ttu-id="326ee-142">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="326ee-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="326ee-143">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="326ee-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
