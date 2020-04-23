---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 035d6439ec90426d7b68e05043ea8b6722f81d28
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121598"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="fd17c-102">Porady: tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="fd17c-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="fd17c-103">Otoki Component Object Model (COM) można tworzyć za pomocą funkcji programu Visual Studio 2005 lub narzędzi .NET Framework Tools Tlbimp. exe i Regasm. exe.</span><span class="sxs-lookup"><span data-stu-id="fd17c-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="fd17c-104">Obie metody generują dwa typy otok COM:</span><span class="sxs-lookup"><span data-stu-id="fd17c-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="fd17c-105">Wywoływanie [otoki środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) z biblioteki typów w celu uruchomienia obiektu com w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="fd17c-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="fd17c-106">Wywoływany przez [com otokę](../../standard/native-interop/com-callable-wrapper.md) z wymaganymi ustawieniami rejestru w celu uruchomienia obiektu zarządzanego w aplikacji natywnej.</span><span class="sxs-lookup"><span data-stu-id="fd17c-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="fd17c-107">W programie Visual Studio 2005 można dodać otokę COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="fd17c-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="fd17c-108">Zawijanie obiektów COM w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="fd17c-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="fd17c-109">Aby utworzyć oddzielną otokę środowiska uruchomieniowego przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd17c-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="fd17c-110">Otwórz projekt dla aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fd17c-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="fd17c-111">W menu **projekt** kliknij polecenie **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="fd17c-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="fd17c-112">W menu **projekt** kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="fd17c-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="fd17c-113">W oknie dialogowym Dodaj odwołanie kliknij kartę **com** , wybierz składnik, którego chcesz użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd17c-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="fd17c-114">W **Eksplorator rozwiązań**Zwróć uwagę, że składnik com jest dodawany do folderu References w projekcie.</span><span class="sxs-lookup"><span data-stu-id="fd17c-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="fd17c-115">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="fd17c-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="fd17c-116">Można rozpocząć od zadeklarowania obiektu, takiego jak `Imports` instrukcja Visual Basic lub `Using` instrukcji dla języka C#.</span><span class="sxs-lookup"><span data-stu-id="fd17c-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="fd17c-117">Jeśli chcesz programować Microsoft Office składniki, najpierw zainstaluj [pakiet redystrybucyjny podstawowych zestawów Międzyoperacyjnych Microsoft Office](https://www.microsoft.com/Download/details.aspx?id=3508).</span><span class="sxs-lookup"><span data-stu-id="fd17c-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="fd17c-118">Aby utworzyć oddzielną otokę środowiska uruchomieniowego przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd17c-118">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="fd17c-119">Uruchom narzędzie [Tlbimp. exe (Importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md) .</span><span class="sxs-lookup"><span data-stu-id="fd17c-119">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="fd17c-120">To narzędzie tworzy zestaw zawierający metadane czasu wykonywania dla typów zdefiniowanych w oryginalnej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="fd17c-120">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="fd17c-121">Zawijaj obiekty zarządzane w aplikacji natywnej</span><span class="sxs-lookup"><span data-stu-id="fd17c-121">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="fd17c-122">Aby utworzyć zawywoływaną przez COM otokę przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd17c-122">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="fd17c-123">Utwórz projekt biblioteki klas dla zarządzanej klasy, która ma być uruchamiana w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="fd17c-123">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="fd17c-124">Klasa musi mieć konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="fd17c-124">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="fd17c-125">Sprawdź, czy dla Twojego zestawu w pliku AssemblyInfo masz pełny numer wersji z czterema częścią.</span><span class="sxs-lookup"><span data-stu-id="fd17c-125">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="fd17c-126">Ta liczba jest wymagana do obsługi wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fd17c-126">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="fd17c-127">Aby uzyskać więcej informacji o numerach wersji, zobacz [wersja zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="fd17c-127">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="fd17c-128">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fd17c-128">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="fd17c-129">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="fd17c-129">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="fd17c-130">Zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="fd17c-130">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="fd17c-131">Podczas kompilowania projektu zestaw jest automatycznie rejestrowany pod kątem współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="fd17c-131">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="fd17c-132">Jeśli tworzysz aplikację natywną w programie Visual Studio 2005, możesz użyć zestawu, klikając pozycję **Dodaj odwołanie** w menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="fd17c-132">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="fd17c-133">Aby utworzyć zawywoływaną przez COM otokę przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd17c-133">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="fd17c-134">Uruchom narzędzie [Regasm. exe (Narzędzie rejestracji zestawów)](../tools/regasm-exe-assembly-registration-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="fd17c-134">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="fd17c-135">To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="fd17c-135">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="fd17c-136">W związku z tym klienci modelu COM mogą w niewidoczny sposób tworzyć klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd17c-136">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="fd17c-137">Zestawu można użyć tak, jakby był natywną klasą COM.</span><span class="sxs-lookup"><span data-stu-id="fd17c-137">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="fd17c-138">Program Regasm. exe można uruchomić na zestawie znajdującym się w dowolnym katalogu, a następnie uruchomić [Gacutil. exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) , aby przenieść go do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="fd17c-138">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="fd17c-139">Przeniesienie zestawu nie unieważnia wpisów rejestru lokalizacji, ponieważ globalna pamięć podręczna zestawów jest zawsze sprawdzana, jeśli zestaw nie został znaleziony w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="fd17c-139">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd17c-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd17c-140">See also</span></span>

- [<span data-ttu-id="fd17c-141">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fd17c-141">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="fd17c-142">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="fd17c-142">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
