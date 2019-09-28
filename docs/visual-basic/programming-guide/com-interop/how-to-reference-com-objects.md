---
title: 'Instrukcje: Odwołuje się do obiektów COM z Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 8e502dc9a279d9271a61fd2cf7a6afb564f09125
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352001"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="8d508-102">Instrukcje: Odwołuje się do obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d508-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="8d508-103">W Visual Basic Dodawanie odwołań do obiektów COM, które mają biblioteki typów, wymaga utworzenia zestawu międzyoperacyjnego dla biblioteki COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="8d508-104">Odwołania do elementów członkowskich obiektu COM są kierowane do zestawu międzyoperacyjnego, a następnie przekazywane do rzeczywistego obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="8d508-105">Odpowiedzi z obiektu COM są kierowane do zestawu międzyoperacyjnego i przekazywane do aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d508-105">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="8d508-106">Można odwołać się do obiektu COM bez użycia zestawu międzyoperacyjnego przez osadzenie informacji o typie dla obiektu COM w zestawie .NET.</span><span class="sxs-lookup"><span data-stu-id="8d508-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="8d508-107">Aby osadzić informacje o typie, ustaw właściwość `Embed Interop Types` na `True` dla odwołania do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="8d508-108">Jeśli kompilujesz przy użyciu kompilatora wiersza polecenia, użyj opcji `/link`, aby odwołać się do biblioteki COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="8d508-109">Aby uzyskać więcej informacji, zobacz [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="8d508-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="8d508-110">Visual Basic automatycznie tworzy zestawy międzyoperacyjności podczas dodawania odwołania do biblioteki typów z zintegrowanego środowiska programistycznego (IDE).</span><span class="sxs-lookup"><span data-stu-id="8d508-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="8d508-111">Podczas pracy z wiersza polecenia można użyć narzędzia Tlbimp do ręcznego tworzenia zestawów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="8d508-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="8d508-112">Aby dodać odwołania do obiektów COM</span><span class="sxs-lookup"><span data-stu-id="8d508-112">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="8d508-113">W menu **projekt** wybierz polecenie **Dodaj odwołanie** , a następnie kliknij kartę **com** w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="8d508-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="8d508-114">Wybierz składnik, którego chcesz użyć z listy obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="8d508-115">Aby uprościć dostęp do zestawu międzyoperacyjnego, Dodaj instrukcję `Imports` na początku klasy lub modułu, w którym będzie używany obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="8d508-116">Poniższy przykład kodu importuje przestrzeń nazw `INKEDLib` dla obiektów, do których odwołuje się biblioteka `Microsoft InkEdit Control 1.0`.</span><span class="sxs-lookup"><span data-stu-id="8d508-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="8d508-117">Aby utworzyć zestaw międzyoperacyjny przy użyciu Tlbimp</span><span class="sxs-lookup"><span data-stu-id="8d508-117">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="8d508-118">Dodaj lokalizację Tlbimp do ścieżki wyszukiwania, jeśli nie jest ona jeszcze częścią ścieżki wyszukiwania i nie znajduje się obecnie w katalogu, w którym się znajduje.</span><span class="sxs-lookup"><span data-stu-id="8d508-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="8d508-119">Wywołaj Tlbimp z wiersza polecenia, dostarczając następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="8d508-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="8d508-120">Nazwa i lokalizacja biblioteki DLL zawierającej bibliotekę typów</span><span class="sxs-lookup"><span data-stu-id="8d508-120">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="8d508-121">Nazwa i lokalizacja przestrzeni nazw, w której należy umieścić informacje</span><span class="sxs-lookup"><span data-stu-id="8d508-121">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="8d508-122">Nazwa i lokalizacja docelowego zestawu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="8d508-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="8d508-123">Poniższy kod zawiera przykład:</span><span class="sxs-lookup"><span data-stu-id="8d508-123">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="8d508-124">Można użyć Tlbimp do tworzenia zestawów międzyoperacyjnych dla bibliotek typów, nawet dla niezarejestrowanych obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="8d508-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="8d508-125">Jednak obiekty COM, do których odwołują się zestawy międzyoperacyjności, muszą być poprawnie zarejestrowane na komputerze, na którym mają być używane.</span><span class="sxs-lookup"><span data-stu-id="8d508-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="8d508-126">Obiekt COM można zarejestrować za pomocą narzędzia regsvr32 dołączonego do systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="8d508-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d508-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d508-127">See also</span></span>

- [<span data-ttu-id="8d508-128">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="8d508-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="8d508-129">Tlbimp.exe (importer biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="8d508-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="8d508-130">Tlbexp.exe (eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="8d508-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="8d508-131">Przewodnik: implementowanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="8d508-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="8d508-132">Rozwiązywanie problemów związanych z współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="8d508-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [<span data-ttu-id="8d508-133">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="8d508-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
