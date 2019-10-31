---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 623df8aa86d25d9a57d3039bee01b0ee39d402a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123937"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="141a1-102">Porady: tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="141a1-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="141a1-103">Otoki Component Object Model (COM) można tworzyć za pomocą funkcji programu Visual Studio 2005 lub narzędzi .NET Framework Tools Tlbimp. exe i Regasm. exe.</span><span class="sxs-lookup"><span data-stu-id="141a1-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="141a1-104">Obie metody generują dwa typy otok COM:</span><span class="sxs-lookup"><span data-stu-id="141a1-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="141a1-105">Wywoływanie [otoki środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) z biblioteki typów w celu uruchomienia obiektu com w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="141a1-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="141a1-106">Wywoływany przez [com otokę](../../standard/native-interop/com-callable-wrapper.md) z wymaganymi ustawieniami rejestru w celu uruchomienia obiektu zarządzanego w aplikacji natywnej.</span><span class="sxs-lookup"><span data-stu-id="141a1-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="141a1-107">W programie Visual Studio 2005 można dodać otokę COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="141a1-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="141a1-108">Zawijanie obiektów COM w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="141a1-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="141a1-109">Aby utworzyć oddzielną otokę środowiska uruchomieniowego przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="141a1-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="141a1-110">Otwórz projekt dla aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="141a1-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="141a1-111">W menu **projekt** kliknij polecenie **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="141a1-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="141a1-112">W menu **projekt** kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="141a1-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="141a1-113">W oknie dialogowym Dodaj odwołanie kliknij kartę **com** , wybierz składnik, którego chcesz użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="141a1-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="141a1-114">W **Eksplorator rozwiązań**Zwróć uwagę, że składnik com jest dodawany do folderu References w projekcie.</span><span class="sxs-lookup"><span data-stu-id="141a1-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="141a1-115">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="141a1-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="141a1-116">Można rozpocząć od zadeklarowania obiektu, takiego jak instrukcja `Imports` dla Visual Basic lub instrukcji `Using` dla C#.</span><span class="sxs-lookup"><span data-stu-id="141a1-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="141a1-117">Jeśli chcesz programować Microsoft Office składniki, najpierw zainstaluj [Microsoft Office podstawowych zestawów międzyoperacyjnych](https://go.microsoft.com/fwlink/?LinkId=50479) (zestawów PIA) z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="141a1-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="141a1-118">W kroku 4 Wybierz najnowszą wersję biblioteki obiektów dostępną dla żądanego produktu pakietu Office, na przykład **bibliotekę obiektów programu Microsoft Word 11,0**.</span><span class="sxs-lookup"><span data-stu-id="141a1-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="141a1-119">Aby utworzyć oddzielną otokę środowiska uruchomieniowego przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="141a1-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="141a1-120">Uruchom narzędzie [Tlbimp. exe (Importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md) .</span><span class="sxs-lookup"><span data-stu-id="141a1-120">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="141a1-121">To narzędzie tworzy zestaw zawierający metadane czasu wykonywania dla typów zdefiniowanych w oryginalnej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="141a1-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="141a1-122">Zawijaj obiekty zarządzane w aplikacji natywnej</span><span class="sxs-lookup"><span data-stu-id="141a1-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="141a1-123">Aby utworzyć zawywoływaną przez COM otokę przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="141a1-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="141a1-124">Utwórz projekt biblioteki klas dla zarządzanej klasy, która ma być uruchamiana w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="141a1-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="141a1-125">Klasa musi mieć konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="141a1-125">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="141a1-126">Sprawdź, czy dla Twojego zestawu w pliku AssemblyInfo masz pełny numer wersji z czterema częścią.</span><span class="sxs-lookup"><span data-stu-id="141a1-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="141a1-127">Ta liczba jest wymagana do obsługi wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="141a1-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="141a1-128">Aby uzyskać więcej informacji o numerach wersji, zobacz [wersja zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="141a1-128">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="141a1-129">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="141a1-129">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="141a1-130">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="141a1-130">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="141a1-131">Zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="141a1-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="141a1-132">Podczas kompilowania projektu zestaw jest automatycznie rejestrowany pod kątem współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="141a1-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="141a1-133">Jeśli tworzysz aplikację natywną w programie Visual Studio 2005, możesz użyć zestawu, klikając pozycję **Dodaj odwołanie** w menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="141a1-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="141a1-134">Aby utworzyć zawywoływaną przez COM otokę przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="141a1-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="141a1-135">Uruchom narzędzie [Regasm. exe (Narzędzie rejestracji zestawów)](../tools/regasm-exe-assembly-registration-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="141a1-135">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="141a1-136">To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="141a1-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="141a1-137">W związku z tym klienci modelu COM mogą w niewidoczny sposób tworzyć klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="141a1-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="141a1-138">Zestawu można użyć tak, jakby był natywną klasą COM.</span><span class="sxs-lookup"><span data-stu-id="141a1-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="141a1-139">Program Regasm. exe można uruchomić na zestawie znajdującym się w dowolnym katalogu, a następnie uruchomić [Gacutil. exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) , aby przenieść go do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="141a1-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="141a1-140">Przeniesienie zestawu nie unieważnia wpisów rejestru lokalizacji, ponieważ globalna pamięć podręczna zestawów jest zawsze sprawdzana, jeśli zestaw nie został znaleziony w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="141a1-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141a1-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="141a1-141">See also</span></span>

- [<span data-ttu-id="141a1-142">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="141a1-142">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="141a1-143">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="141a1-143">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
