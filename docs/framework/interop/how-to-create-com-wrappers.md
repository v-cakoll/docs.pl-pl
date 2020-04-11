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
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="0ce30-102">Porady: tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="0ce30-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="0ce30-103">Otoki modelu com (Component Object Model) można tworzyć przy użyciu funkcji programu Visual Studio 2005 lub narzędzi .NET Framework Tlbimp.exe i Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="0ce30-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="0ce30-104">Obie metody generują dwa typy otoki COM:</span><span class="sxs-lookup"><span data-stu-id="0ce30-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="0ce30-105">[Otoka wywołalna w czasie wykonywania](../../standard/native-interop/runtime-callable-wrapper.md) z biblioteki typów do uruchomienia obiektu COM w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0ce30-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="0ce30-106">Otoka [rozpisywalna com](../../standard/native-interop/com-callable-wrapper.md) z wymaganymi ustawieniami rejestru do uruchomienia obiektu zarządzanego w aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="0ce30-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="0ce30-107">W programie Visual Studio 2005 można dodać otoki COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="0ce30-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="0ce30-108">Zawijanie obiektów COM w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="0ce30-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="0ce30-109">Aby utworzyć otokę wywoływaną w czasie wykonywania przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ce30-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="0ce30-110">Otwórz projekt dla aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0ce30-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="0ce30-111">W menu **Projekt** kliknij polecenie **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="0ce30-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="0ce30-112">W menu **Projekt** kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="0ce30-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="0ce30-113">W oknie dialogowym Dodawanie odwołania kliknij kartę **COM,** wybierz składnik, którego chcesz użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0ce30-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="0ce30-114">W **Eksploratorze rozwiązań**należy zauważyć, że składnik COM jest dodawany do folderu Odwołania w projekcie.</span><span class="sxs-lookup"><span data-stu-id="0ce30-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="0ce30-115">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="0ce30-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="0ce30-116">Można rozpocząć od deklarowania obiektu, na `Imports` przykład z instrukcją dla języka Visual Basic lub instrukcją `Using` dla języka C#.</span><span class="sxs-lookup"><span data-stu-id="0ce30-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="0ce30-117">Jeśli chcesz zaprogramować składniki pakietu Microsoft Office, najpierw zainstaluj [redystrybucyjne zestawy interpli pakietu Microsoft Office.](https://www.microsoft.com/Download/details.aspx?id=3508)</span><span class="sxs-lookup"><span data-stu-id="0ce30-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="0ce30-118">Aby utworzyć otokę wywoływaną w czasie wykonywania przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ce30-118">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="0ce30-119">Uruchom narzędzie [Tlbimp.exe (Importer biblioteki typów).](../tools/tlbimp-exe-type-library-importer.md)</span><span class="sxs-lookup"><span data-stu-id="0ce30-119">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="0ce30-120">To narzędzie tworzy zestaw zawierający metadane w czasie wykonywania dla typów zdefiniowanych w oryginalnej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="0ce30-120">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="0ce30-121">Zawijanie obiektów zarządzanych w aplikacji macierzystej</span><span class="sxs-lookup"><span data-stu-id="0ce30-121">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="0ce30-122">Aby utworzyć otokę wywoływaną przez COM przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ce30-122">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="0ce30-123">Utwórz projekt biblioteki klas dla klasy zarządzanej, którą chcesz uruchomić w kodzie macierzystym.</span><span class="sxs-lookup"><span data-stu-id="0ce30-123">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="0ce30-124">Klasa musi mieć konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="0ce30-124">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="0ce30-125">Sprawdź, czy masz pełny czteroczęściowy numer wersji dla złożenia w pliku AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="0ce30-125">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="0ce30-126">Ten numer jest wymagany do obsługi przechowywania wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0ce30-126">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="0ce30-127">Aby uzyskać więcej informacji na temat numerów wersji, zobacz [Przechowywanie wersji zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="0ce30-127">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="0ce30-128">W menu **Projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0ce30-128">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="0ce30-129">Kliknij kartę **Kompilowanie.**</span><span class="sxs-lookup"><span data-stu-id="0ce30-129">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="0ce30-130">Zaznacz pole wyboru **Zarejestruj się dla współdziałania COM.**</span><span class="sxs-lookup"><span data-stu-id="0ce30-130">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="0ce30-131">Podczas tworzenia projektu, zestaw jest automatycznie rejestrowany dla com interop.</span><span class="sxs-lookup"><span data-stu-id="0ce30-131">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="0ce30-132">Jeśli budujesz aplikację natywną w programie Visual Studio 2005, można użyć zestawu, klikając **dodaj odwołanie** w menu **projektu.**</span><span class="sxs-lookup"><span data-stu-id="0ce30-132">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="0ce30-133">Aby utworzyć otokę wywoływaną przez COM przy użyciu narzędzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ce30-133">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="0ce30-134">Uruchom narzędzie [Regasm.exe (narzędzie rejestracji zestawu).](../tools/regasm-exe-assembly-registration-tool.md)</span><span class="sxs-lookup"><span data-stu-id="0ce30-134">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="0ce30-135">To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="0ce30-135">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="0ce30-136">W rezultacie klienci COM mogą tworzyć klasy .NET Framework w sposób przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="0ce30-136">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="0ce30-137">Można użyć zestawu tak, jakby był natywną klasą COM.</span><span class="sxs-lookup"><span data-stu-id="0ce30-137">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="0ce30-138">Program Regasm.exe można uruchomić w zestawie znajdującym się w dowolnym katalogu, a następnie uruchomić [plik Gacutil.exe (Narzędzie globalnej pamięci podręcznej zestawów),](../tools/gacutil-exe-gac-tool.md) aby przenieść go do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="0ce30-138">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="0ce30-139">Przenoszenie zestawu nie unieważnia wpisów rejestru lokalizacji, ponieważ globalna pamięć podręczna zestawów jest zawsze sprawdzana, jeśli zestaw nie zostanie znaleziony gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="0ce30-139">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce30-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ce30-140">See also</span></span>

- [<span data-ttu-id="0ce30-141">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0ce30-141">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="0ce30-142">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="0ce30-142">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
