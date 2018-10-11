---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14bf011c3711a267b8cf5a1fc0497a347468387d
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087820"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="0ca2f-102">Porady: tworzenie otok COM</span><span class="sxs-lookup"><span data-stu-id="0ca2f-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="0ca2f-103">Otoki Component Object Model (COM) można utworzyć za pomocą funkcji Visual Studio 2005 lub narzędzi programu .NET Framework, Tlbimp.exe i Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="0ca2f-104">Obie metody wygenerować dwa typy otok COM:</span><span class="sxs-lookup"><span data-stu-id="0ca2f-104">Both methods generate two types of COM wrappers:</span></span>

-   <span data-ttu-id="0ca2f-105">A [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) z biblioteki typów, aby uruchomić obiektów COM w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

-   <span data-ttu-id="0ca2f-106">A [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md) za pomocą ustawień rejestru wymagane do uruchamiania zarządzanego obiektu w aplikacji natywnej.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="0ca2f-107">W programie Visual Studio 2005 można dodać otoki COM jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="0ca2f-108">Zawiń obiektów COM w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="0ca2f-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="0ca2f-109">Aby utworzyć wywoływana otoka środowiska uruchomieniowego przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ca2f-109">To create a runtime callable wrapper using Visual Studio</span></span>

1.  <span data-ttu-id="0ca2f-110">Otwórz projekt dla aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-110">Open the project for your managed application.</span></span>

2.  <span data-ttu-id="0ca2f-111">Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-111">On the **Project** menu, click **Show All Files**.</span></span>

3.  <span data-ttu-id="0ca2f-112">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-112">On the **Project** menu, click **Add Reference**.</span></span>

4.  <span data-ttu-id="0ca2f-113">W oknie dialogowym Dodaj odwołanie, kliknij przycisk **COM** , a następnie wybierz składnik, należy użyć, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="0ca2f-114">W **Eksploratora rozwiązań**, należy pamiętać, że składnik COM został dodany do folderu odwołań w projekcie.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="0ca2f-115">Teraz można napisać kod, aby uzyskać dostęp do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="0ca2f-116">Możesz rozpocząć od zadeklarowania obiektu, takie jak za pomocą `Imports` poufności informacji dotyczące [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] lub `Using` poufności informacji dotyczące [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ca2f-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="0ca2f-117">Jeśli chcesz program Microsoft Office składniki, najpierw zainstaluj [podstawowe zestawy międzyoperacyjne pakietu Office Microsoft](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="0ca2f-118">W kroku 4, wybierz najnowszą dostępną dla produktu Office ma, takich jak biblioteki obiektów **Biblioteka obiektów programu Microsoft Word 11.0**.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="0ca2f-119">Aby utworzyć wywoływana otoka środowiska uruchomieniowego przy użyciu narzędzi programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ca2f-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="0ca2f-120">Uruchom [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="0ca2f-121">To narzędzie tworzy zestaw, który zawiera metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="0ca2f-122">OPAKOWYWANIE zarządzanych obiektów w aplikacji macierzystej</span><span class="sxs-lookup"><span data-stu-id="0ca2f-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="0ca2f-123">Aby utworzyć wywołalne opakowanie COM za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ca2f-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="0ca2f-124">Utwórz projekt biblioteki klas dla zarządzanej klasy, która ma zostać uruchomiony w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="0ca2f-125">Klasa musi mieć domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="0ca2f-126">Sprawdź, czy masz pełną Czteroczęściowy numer wersji zestawu w pliku AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="0ca2f-127">Ta liczba jest wymagany do obsługi przechowywania wersji w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="0ca2f-128">Aby uzyskać więcej informacji na temat numerów wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="0ca2f-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="0ca2f-129">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0ca2f-130">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="0ca2f-131">Wybierz **Zarejestruj dla współdziałania COM** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="0ca2f-132">Podczas kompilowania projektu zestawu jest automatycznie rejestrowane dla współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="0ca2f-133">Jeśli tworzysz natywnych aplikacji w programie Visual Studio 2005, można użyć zestawu, klikając **Dodaj odwołanie** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="0ca2f-134">Aby utworzyć wywołalne opakowanie COM za pomocą narzędzi programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ca2f-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="0ca2f-135">Uruchom [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="0ca2f-136">To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="0ca2f-137">W rezultacie klientów modelu COM może przezroczyste Tworzenie klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="0ca2f-138">Można użyć zestawu, tak jakby natywnych klasa COM.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="0ca2f-139">Uruchamianie Regasm.exe na zestawu znajdującego się w dowolnym katalogu, a następnie uruchom [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) przenieść je do globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="0ca2f-140">Przenoszenie zestawu nie unieważnia wpisy rejestru lokalizacji, ponieważ w globalnej pamięci podręcznej jest badany zawsze, jeśli zestaw nie zostanie znaleziony gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="0ca2f-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca2f-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ca2f-141">See also</span></span>  

- [<span data-ttu-id="0ca2f-142">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0ca2f-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
- [<span data-ttu-id="0ca2f-143">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="0ca2f-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)