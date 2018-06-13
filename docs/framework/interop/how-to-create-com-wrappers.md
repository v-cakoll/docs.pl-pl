---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4deb355a7b523437ae31a1d2b9c79e3b8d4f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391228"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="6f40c-102">Porady: tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="6f40c-102">How to: Create COM Wrappers</span></span>
<span data-ttu-id="6f40c-103">Otoki składnika modelu COM (Object) można tworzyć przy użyciu [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] funkcji lub .NET Framework Tlbimp.exe i Regasm.exe narzędzi.</span><span class="sxs-lookup"><span data-stu-id="6f40c-103">You can create Component Object Model (COM) wrappers by using [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="6f40c-104">Obie metody generowania otoki COM dwa typy:</span><span class="sxs-lookup"><span data-stu-id="6f40c-104">Both methods generate two types of COM wrappers:</span></span>  
  
-   <span data-ttu-id="6f40c-105">A [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) z biblioteki typów do uruchamiania obiektów COM w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6f40c-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>  
  
-   <span data-ttu-id="6f40c-106">A [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md) przy użyciu ustawień wymaganych do uruchomienia zarządzanego obiektu w natywnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f40c-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>  
  
 <span data-ttu-id="6f40c-107">W [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], można dodać otoki COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="6f40c-107">In [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can add the COM wrapper as a reference to your project.</span></span>  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a><span data-ttu-id="6f40c-108">Zawijanie obiektów COM w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="6f40c-108">Wrapping COM Objects in a Managed Application</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="6f40c-109">Aby utworzyć wywoływana otoka środowiska uruchomieniowego za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f40c-109">To create a runtime callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="6f40c-110">Otwórz projekt aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="6f40c-110">Open the project for your managed application.</span></span>  
  
2.  <span data-ttu-id="6f40c-111">Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="6f40c-111">On the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="6f40c-112">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="6f40c-112">On the **Project** menu, click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="6f40c-113">W oknie dialogowym Dodawanie odwołania, kliknij przycisk **COM** , a następnie wybierz składnik, należy użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f40c-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>  
  
     <span data-ttu-id="6f40c-114">W **Eksploratora rozwiązań**, należy pamiętać, że składnik modelu COM został dodany do folderu odwołań w projekcie.</span><span class="sxs-lookup"><span data-stu-id="6f40c-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>  
  
 <span data-ttu-id="6f40c-115">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="6f40c-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="6f40c-116">Możesz rozpocząć od zadeklarowania obiektów, takich jak z `Imports` instrukcji dla [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] lub `Using` instrukcji dla [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f40c-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f40c-117">Jeśli chcesz składniki programu Microsoft Office, najpierw zainstaluj [podstawowe zestawy międzyoperacyjne pakietu Office Microsoft](http://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="6f40c-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](http://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="6f40c-118">W kroku 4, wybierz najnowszą wersję biblioteki dostępne dla produktów Office ma, takich jak **Microsoft Word 11.0 biblioteki**.</span><span class="sxs-lookup"><span data-stu-id="6f40c-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="6f40c-119">Aby utworzyć wywoływana otoka środowiska uruchomieniowego za pomocą narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f40c-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="6f40c-120">Uruchom [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6f40c-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="6f40c-121">To narzędzie tworzy zestawu zawierającego metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnym biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="6f40c-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a><span data-ttu-id="6f40c-122">Zawijanie zarządzanych obiektów w aplikacji natywnej</span><span class="sxs-lookup"><span data-stu-id="6f40c-122">Wrapping Managed Objects in a Native Application</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="6f40c-123">Aby utworzyć wywoływana otoka COM za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f40c-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="6f40c-124">Tworzenie projektu biblioteki klas zarządzanych klasy, która ma zostać uruchomione w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="6f40c-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="6f40c-125">Klasa musi mieć konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="6f40c-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="6f40c-126">Sprawdź, czy Zakończenie Czteroczęściowy numer wersji dla programu zestawu w pliku AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="6f40c-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="6f40c-127">Ta liczba jest wymagana do obsługi przechowywania wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6f40c-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="6f40c-128">Aby uzyskać więcej informacji o numerach wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="6f40c-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="6f40c-129">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6f40c-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="6f40c-130">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="6f40c-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="6f40c-131">Wybierz **Zarejestruj dla międzyoperacyjności z modelem COM** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="6f40c-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="6f40c-132">Podczas kompilowania projektu zestawu jest automatycznie rejestrowana COM interop.</span><span class="sxs-lookup"><span data-stu-id="6f40c-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="6f40c-133">Jeśli tworzysz natywnych aplikacji [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], można użyć zestawu, klikając **Dodaj odwołanie** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="6f40c-133">If you are building a native application in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="6f40c-134">Aby utworzyć wywoływana otoka COM za pomocą narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f40c-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="6f40c-135">Uruchom [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6f40c-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
 <span data-ttu-id="6f40c-136">To narzędzie umożliwia odczytanie metadanych zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="6f40c-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="6f40c-137">W związku z tym klienci COM tworzyć .NET Framework klasy przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="6f40c-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="6f40c-138">Tak, jakby była natywnego klasy COM, można użyć zestawu.</span><span class="sxs-lookup"><span data-stu-id="6f40c-138">You can use the assembly as if it were a native COM class.</span></span>  
  
 <span data-ttu-id="6f40c-139">Uruchom Regasm.exe w zestawie znajduje się w dowolnym katalogu, a następnie uruchom [Gacutil.exe (narzędzie globalnej pamięci podręcznej zestawów)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) Aby przenieść ją do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="6f40c-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="6f40c-140">Przenoszenie zestawu unieważnia wpisy rejestru lokalizacji, ponieważ w pamięci podręcznej GAC są zawsze przeanalizować, jeśli zestaw nie znajduje się w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="6f40c-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f40c-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f40c-141">See Also</span></span>  
 [<span data-ttu-id="6f40c-142">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6f40c-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="6f40c-143">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="6f40c-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
