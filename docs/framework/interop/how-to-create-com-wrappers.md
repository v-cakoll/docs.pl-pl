---
title: 'Instrukcje: Tworzenie otok COM'
description: Tworzenie otok Component Object Model (COM) przy użyciu programu Visual Studio lub narzędzi .NET (Tlbimp.exe i Regasm.exe). Obie metody generują dwa typy otok COM.
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 286526c710287e6efa3e49a7f7c55e3687076e29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617395"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="1729c-104">Instrukcje: Tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="1729c-104">How to: Create COM Wrappers</span></span>

<span data-ttu-id="1729c-105">Otoki Component Object Model (COM) można tworzyć za pomocą funkcji programu Visual Studio 2005 lub narzędzi .NET Framework Tlbimp.exe i Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="1729c-105">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="1729c-106">Obie metody generują dwa typy otok COM:</span><span class="sxs-lookup"><span data-stu-id="1729c-106">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="1729c-107">Wywoływanie [otoki środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) z biblioteki typów w celu uruchomienia obiektu com w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="1729c-107">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="1729c-108">Wywoływany przez [com otokę](../../standard/native-interop/com-callable-wrapper.md) z wymaganymi ustawieniami rejestru w celu uruchomienia obiektu zarządzanego w aplikacji natywnej.</span><span class="sxs-lookup"><span data-stu-id="1729c-108">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="1729c-109">W programie Visual Studio 2005 można dodać otokę COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="1729c-109">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="1729c-110">Zawijanie obiektów COM w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="1729c-110">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="1729c-111">Aby utworzyć oddzielną otokę środowiska uruchomieniowego przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1729c-111">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="1729c-112">Otwórz projekt dla aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="1729c-112">Open the project for your managed application.</span></span>

2. <span data-ttu-id="1729c-113">W menu **projekt** kliknij polecenie **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="1729c-113">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="1729c-114">W menu **projekt** kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="1729c-114">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="1729c-115">W oknie dialogowym Dodaj odwołanie kliknij kartę **com** , wybierz składnik, którego chcesz użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="1729c-115">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="1729c-116">W **Eksplorator rozwiązań**Zwróć uwagę, że składnik com jest dodawany do folderu References w projekcie.</span><span class="sxs-lookup"><span data-stu-id="1729c-116">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="1729c-117">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="1729c-117">You can now write code to access the COM object.</span></span> <span data-ttu-id="1729c-118">Można rozpocząć od zadeklarowania obiektu, takiego jak `Imports` instrukcja Visual Basic lub `Using` instrukcji dla języka C#.</span><span class="sxs-lookup"><span data-stu-id="1729c-118">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="1729c-119">Jeśli chcesz programować Microsoft Office składniki, najpierw zainstaluj [pakiet redystrybucyjny podstawowych zestawów Międzyoperacyjnych Microsoft Office](https://www.microsoft.com/Download/details.aspx?id=3508).</span><span class="sxs-lookup"><span data-stu-id="1729c-119">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="1729c-120">Aby utworzyć oddzielną otokę środowiska uruchomieniowego przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1729c-120">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="1729c-121">Uruchom narzędzie [Tlbimp.exe (Importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md) .</span><span class="sxs-lookup"><span data-stu-id="1729c-121">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="1729c-122">To narzędzie tworzy zestaw zawierający metadane czasu wykonywania dla typów zdefiniowanych w oryginalnej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="1729c-122">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="1729c-123">Zawijaj obiekty zarządzane w aplikacji natywnej</span><span class="sxs-lookup"><span data-stu-id="1729c-123">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="1729c-124">Aby utworzyć zawywoływaną przez COM otokę przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1729c-124">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="1729c-125">Utwórz projekt biblioteki klas dla zarządzanej klasy, która ma być uruchamiana w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="1729c-125">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="1729c-126">Klasa musi mieć konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="1729c-126">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="1729c-127">Sprawdź, czy dla Twojego zestawu w pliku AssemblyInfo masz pełny numer wersji z czterema częścią.</span><span class="sxs-lookup"><span data-stu-id="1729c-127">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="1729c-128">Ta liczba jest wymagana do obsługi wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1729c-128">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="1729c-129">Aby uzyskać więcej informacji o numerach wersji, zobacz [wersja zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="1729c-129">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="1729c-130">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1729c-130">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="1729c-131">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="1729c-131">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="1729c-132">Zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="1729c-132">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="1729c-133">Podczas kompilowania projektu zestaw jest automatycznie rejestrowany pod kątem współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="1729c-133">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="1729c-134">Jeśli tworzysz aplikację natywną w programie Visual Studio 2005, możesz użyć zestawu, klikając pozycję **Dodaj odwołanie** w menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="1729c-134">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="1729c-135">Aby utworzyć zawywoływaną przez COM otokę przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1729c-135">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="1729c-136">Uruchom narzędzie [Regasm.exe (Narzędzie rejestracji zestawów)](../tools/regasm-exe-assembly-registration-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="1729c-136">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="1729c-137">To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="1729c-137">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="1729c-138">W związku z tym klienci modelu COM mogą w niewidoczny sposób tworzyć klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1729c-138">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="1729c-139">Zestawu można użyć tak, jakby był natywną klasą COM.</span><span class="sxs-lookup"><span data-stu-id="1729c-139">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="1729c-140">Można uruchomić Regasm.exe w zestawie znajdującym się w dowolnym katalogu, a następnie uruchomić [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) , aby przenieść go do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1729c-140">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="1729c-141">Przeniesienie zestawu nie unieważnia wpisów rejestru lokalizacji, ponieważ globalna pamięć podręczna zestawów jest zawsze sprawdzana, jeśli zestaw nie został znaleziony w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1729c-141">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1729c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1729c-142">See also</span></span>

- [<span data-ttu-id="1729c-143">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1729c-143">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="1729c-144">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="1729c-144">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
