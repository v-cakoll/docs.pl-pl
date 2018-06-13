---
title: -link (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 95c528c4d686c44d0d77d1f55833be75ab14f8bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656272"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="a7173-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7173-102">-link (Visual Basic)</span></span>
<span data-ttu-id="a7173-103">Powoduje, że kompilator, aby udostępnić informacje o typie modelu COM w określonych zestawów do projektu, które są aktualnie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a7173-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7173-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7173-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7173-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a7173-105">Arguments</span></span>  
  
|<span data-ttu-id="a7173-106">Termin</span><span class="sxs-lookup"><span data-stu-id="a7173-106">Term</span></span>|<span data-ttu-id="a7173-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="a7173-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="a7173-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7173-108">Required.</span></span> <span data-ttu-id="a7173-109">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="a7173-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="a7173-110">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="a7173-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7173-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7173-111">Remarks</span></span>  
 <span data-ttu-id="a7173-112">`-link` Opcja umożliwia wdrażanie aplikacji, która zawiera osadzone informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="a7173-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="a7173-113">Aplikacja może następnie używać typów w zestawie środowiska uruchomieniowego, które implementują informacji osadzonym typem bez konieczności odwołanie do zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="a7173-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="a7173-114">Jeśli w różnych wersjach zestawu środowiska wykonawczego są publikowane, aplikacji, który zawiera informacje o osadzonym typem może współpracować z różnych wersji bez konieczności ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="a7173-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="a7173-115">Na przykład zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="a7173-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="a7173-116">Przy użyciu `-link` opcja jest szczególnie przydatne podczas pracy z COM interop.</span><span class="sxs-lookup"><span data-stu-id="a7173-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="a7173-117">Można osadzić typów COM, aby aplikacja nie wymaga już podstawowy zestaw międzyoperacyjny (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="a7173-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="a7173-118">`-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie COM z przywoływanego zestawu międzyoperacyjnego na wynikowej skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a7173-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="a7173-119">Typ modelu COM jest identyfikowany przez wartość identyfikatora CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="a7173-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="a7173-120">W związku z tym aplikację można uruchomić na komputerze docelowym, który zainstalował takich samych typach modelu COM przy użyciu tej samej wartości identyfikatora CLSID.</span><span class="sxs-lookup"><span data-stu-id="a7173-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="a7173-121">Dobrym przykładem są aplikacje, które automatyzują Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a7173-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="a7173-122">Ponieważ aplikacji, takich jak Office zazwyczaj zachować taką samą wartość identyfikatora CLSID w różnych wersjach, aplikacja może używać wskazanych typów COM, jak długo jako .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym i aplikacja korzysta z metod, właściwości lub zdarzenia, które są objęte wskazanych typów COM.</span><span class="sxs-lookup"><span data-stu-id="a7173-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="a7173-123">`-link` Opcja osadza interfejsów, struktur i delegatów.</span><span class="sxs-lookup"><span data-stu-id="a7173-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="a7173-124">Osadzanie klasy COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a7173-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7173-125">Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a7173-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="a7173-126">Podjęto próbę utworzenia wystąpienia typu osadzonego modelu COM za pomocą klasy CoClass powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="a7173-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="a7173-127">Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu danych i ustaw `Embed Interop Types` właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="a7173-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="a7173-128">Wartość domyślna dla `Embed Interop Types` właściwość jest **false**.</span><span class="sxs-lookup"><span data-stu-id="a7173-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="a7173-129">Gdy łącze do zestawu COM (zestaw A) które odwołuje się do innego zestawu COM (zestaw B), należy także łącze do zestawu B, jeśli spełniony jest jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a7173-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="a7173-130">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="a7173-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="a7173-131">Pola, właściwości, zdarzenia lub metodę, która ma zwracany typ lub parametr typu z B zestawu jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="a7173-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="a7173-132">Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) Aby określić katalog, w którym znajduje się co najmniej jednego odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="a7173-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="a7173-133">Podobnie jak [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora, `-link` — opcja kompilatora używa Vbc.rsp plik odpowiedzi, który odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="a7173-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="a7173-134">Użyj [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opcję kompilatora, jeśli nie chcesz kompilatora, aby użyć pliku Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a7173-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="a7173-135">Krótka forma z `-link` jest `-l`.</span><span class="sxs-lookup"><span data-stu-id="a7173-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="a7173-136">Typy ogólne i osadzone typy</span><span class="sxs-lookup"><span data-stu-id="a7173-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="a7173-137">W poniższych sekcjach opisano ograniczenia przy użyciu typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a7173-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="a7173-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="a7173-138">Generic Interfaces</span></span>  
 <span data-ttu-id="a7173-139">Nie można używać interfejsów ogólnych osadzonych z zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a7173-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="a7173-140">Przedstawiono to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7173-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="a7173-141">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="a7173-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="a7173-142">Typy, które mają parametru ogólnego, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zewnętrznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a7173-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="a7173-143">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="a7173-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="a7173-144">Rozważmy na przykład <xref:Microsoft.Office.Interop.Excel.Range> interfejs, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="a7173-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="a7173-145">Jeśli biblioteki osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca wartość typu ogólnego, który ma parametr typu jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a7173-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="a7173-146">W poniższym przykładzie kodu klienta można wywołać metodę, która zwraca <xref:System.Collections.IList> ogólny interfejs bez błędów.</span><span class="sxs-lookup"><span data-stu-id="a7173-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="a7173-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7173-147">Example</span></span>  
 <span data-ttu-id="a7173-148">Poniższe polecenie kompiluje plik źródłowy `OfficeApp.vb` i odwołuje się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="a7173-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7173-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7173-149">See Also</span></span>  
 [<span data-ttu-id="a7173-150">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7173-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a7173-151">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="a7173-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="a7173-152">-odwołania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7173-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="a7173-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="a7173-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="a7173-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="a7173-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [<span data-ttu-id="a7173-155">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="a7173-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="a7173-156">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="a7173-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
