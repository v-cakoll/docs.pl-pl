---
title: 'Porady: odwołania do obiektów COM z Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f6f7b4887e2cfba65da7a7a890b78c3d6a8508f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="c21fc-102">Porady: odwołania do obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c21fc-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="c21fc-103">W języku Visual Basic Dodawanie odwołań do obiektów COM, które mają bibliotek typów wymaga utworzenia zestawu międzyoperacyjnego dla biblioteki COM.</span><span class="sxs-lookup"><span data-stu-id="c21fc-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="c21fc-104">Odwołania do elementów członkowskich obiektu COM są kierowane do zestawu międzyoperacyjnego, a następnie przekazywane do rzeczywistego obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="c21fc-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="c21fc-105">Odpowiedzi z obiektu COM są kierowane do zestawu międzyoperacyjnego i przekazywane do Twojej [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c21fc-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="c21fc-106">Obiekt COM można odwoływać się bez użycia zestawu międzyoperacyjnego osadzanie informacji o typie dla obiekt COM w ramach zestawu .NET.</span><span class="sxs-lookup"><span data-stu-id="c21fc-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="c21fc-107">Osadzanie informacji o typie, ustaw `Embed Interop Types` właściwości `True` dla odwołania do obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="c21fc-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="c21fc-108">Jeśli kompilacja przy użyciu kompilatora wiersza polecenia, użyj `/link` opcję, aby odwołać biblioteki COM.</span><span class="sxs-lookup"><span data-stu-id="c21fc-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="c21fc-109">Aby uzyskać więcej informacji, zobacz [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="c21fc-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="c21fc-110">Visual Basic automatycznie tworzy zestawy międzyoperacyjne podczas dodawania odwołania do biblioteki typów z zintegrowane środowisko programistyczne (IDE).</span><span class="sxs-lookup"><span data-stu-id="c21fc-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="c21fc-111">Podczas pracy z poziomu wiersza polecenia, można użyć narzędzia Tlbimp ręcznie utworzyć zestawy międzyoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="c21fc-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="c21fc-112">Aby dodać odwołania do obiektów COM</span><span class="sxs-lookup"><span data-stu-id="c21fc-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="c21fc-113">Na **projektu** menu, wybierz **Dodaj odwołanie** , a następnie kliknij przycisk **COM** karty w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="c21fc-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="c21fc-114">Wybierz składnik, który ma być używany z listy obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="c21fc-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="c21fc-115">Aby ułatwić dostęp do zestawu międzyoperacyjnego, Dodaj `Imports` instrukcji na początku klasę lub moduł, w którym będzie używać obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="c21fc-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="c21fc-116">Na przykład poniższy przykładowy kod importuje przestrzeń nazw `INKEDLib` dla obiektów, do którego odwołuje się `Microsoft InkEdit Control 1.0` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c21fc-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="c21fc-117">Aby utworzyć zestaw międzyoperacyjny przy użyciu Tlbimp</span><span class="sxs-lookup"><span data-stu-id="c21fc-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="c21fc-118">Dodaj lokalizację Tlbimp do ścieżki wyszukiwania, jeśli nie jest już częścią ścieżki wyszukiwania i nie jesteś obecnie w katalogu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="c21fc-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="c21fc-119">Wywołanie Tlbimp z wiersza polecenia, podając następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="c21fc-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="c21fc-120">Nazwa i lokalizacja biblioteki DLL zawierającej biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="c21fc-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="c21fc-121">Nazwa i lokalizacja przestrzeni nazw rozmieszczenia danych</span><span class="sxs-lookup"><span data-stu-id="c21fc-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="c21fc-122">Nazwy i lokalizacji docelowej zestawu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="c21fc-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="c21fc-123">Poniższy kod stanowi przykład:</span><span class="sxs-lookup"><span data-stu-id="c21fc-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="c21fc-124">Tlbimp służy do tworzenia zestawy międzyoperacyjne dla biblioteki typów, nawet w przypadku obiektów COM wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="c21fc-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="c21fc-125">Jednak z obiektami COM odwołuje się zestawy międzyoperacyjne musi być poprawnie zarejestrowany na komputerze, gdy są do użycia.</span><span class="sxs-lookup"><span data-stu-id="c21fc-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="c21fc-126">Obiekt COM można zarejestrować za pomocą narzędzia Regsvr32 zawarte w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="c21fc-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c21fc-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c21fc-127">See Also</span></span>  
 [<span data-ttu-id="c21fc-128">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="c21fc-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="c21fc-129">Tlbimp.exe (importer biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="c21fc-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="c21fc-130">Tlbexp.exe (eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="c21fc-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="c21fc-131">Przewodnik: wdrażanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="c21fc-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="c21fc-132">Rozwiązywanie problemów związanych z współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="c21fc-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="c21fc-133">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="c21fc-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
