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
ms.openlocfilehash: a9ebb05ca3230ff5f838e56dcc004c1958f8c86a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736631"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="2cd7f-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd7f-102">-link (Visual Basic)</span></span>
<span data-ttu-id="2cd7f-103">Powoduje, że kompilator udostępnia informacje o typie modelu COM w określonych zestawach do projektu, który obecnie kompilacja.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cd7f-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cd7f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2cd7f-105">Arguments</span></span>  
  
|<span data-ttu-id="2cd7f-106">Termin</span><span class="sxs-lookup"><span data-stu-id="2cd7f-106">Term</span></span>|<span data-ttu-id="2cd7f-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="2cd7f-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2cd7f-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-108">Required.</span></span> <span data-ttu-id="2cd7f-109">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2cd7f-110">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd7f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cd7f-111">Remarks</span></span>  
 <span data-ttu-id="2cd7f-112">`-link` Opcja służy do wdrażania aplikacji, która zawiera osadzone informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="2cd7f-113">Aplikacja następnie można użyć typów w zestawie środowiska uruchomieniowego, które implementują informacje o typie osadzony bez odwołania do zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="2cd7f-114">Jeśli różne wersje zestawów środowiska uruchomieniowego są publikowane, aplikacji, która zawiera informacje o typie osadzony pracować z różnymi wersjami bez konieczności zostać zrekompilowane.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="2cd7f-115">Aby uzyskać przykład, zobacz [instruktażu: Osadzanie typów z zarządzanych zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2cd7f-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>  
  
 <span data-ttu-id="2cd7f-116">Za pomocą `-link` opcja jest szczególnie przydatna w przypadku, gdy pracujesz za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="2cd7f-117">Można osadzić typów modelu COM, dzięki czemu aplikacja nie wymaga już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="2cd7f-118">`-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie modelu COM z odwołania zestawu międzyoperacyjnego wynikowy kod skompilowany.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="2cd7f-119">Typ COM jest identyfikowany przez wartość identyfikatora CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="2cd7f-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="2cd7f-120">W rezultacie aplikację można uruchomić na komputerze docelowym, w której zainstalowano te same typy modelu COM za pomocą tych samych wartości identyfikatora CLSID.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="2cd7f-121">Aplikacje, które automatyzują Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="2cd7f-122">Ponieważ aplikacji, takich jak Office zwykle zachować tę samą wartość identyfikatora CLSID różnych wersji, aplikacja może używać typów modelu COM, jak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a Twoja aplikacja używa metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="2cd7f-123">`-link` Opcja osadza interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="2cd7f-124">Osadzanie klasy COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cd7f-125">Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="2cd7f-126">Próba utworzenia wystąpienia typu osadzonego modelu COM za pomocą wspólna spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="2cd7f-127">Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="2cd7f-128">Wartość domyślna dla `Embed Interop Types` właściwość **false**.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="2cd7f-129">Jeśli łączysz się do zestawu COM (Assembly A) która sama odwołuje się do innego zestawu modelu COM (Assembly B), musisz również link do zestawu B, jeśli jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2cd7f-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="2cd7f-130">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="2cd7f-131">Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2cd7f-132">Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2cd7f-133">Podobnie jak [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora, `-link` — opcja kompilatora korzysta z pliku odpowiedzi Vbc.rsp odwołania często używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="2cd7f-134">Użyj [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opcji kompilatora, jeśli nie chcesz, aby kompilator korzystać soubor Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="2cd7f-135">Krótkiej formy `-link` jest `-l`.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="2cd7f-136">Typy ogólne i osadzone typy</span><span class="sxs-lookup"><span data-stu-id="2cd7f-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="2cd7f-137">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="2cd7f-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="2cd7f-138">Generic Interfaces</span></span>  
 <span data-ttu-id="2cd7f-139">Nie można używać interfejsów ogólnych, które są osadzone w zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="2cd7f-140">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="2cd7f-141">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="2cd7f-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="2cd7f-142">Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zestawu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="2cd7f-143">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="2cd7f-144">Na przykład, rozważmy <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="2cd7f-145">Jeśli biblioteka osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ ogólny, który ma parametr, którego typ jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu i metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="2cd7f-146">W poniższym przykładzie, kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs ogólny bez błędów.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cd7f-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="2cd7f-147">Example</span></span>  
 <span data-ttu-id="2cd7f-148">Następujące polecenie kompiluje plik źródłowy `OfficeApp.vb` i odwoływać się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="2cd7f-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cd7f-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cd7f-149">See also</span></span>

- [<span data-ttu-id="2cd7f-150">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2cd7f-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2cd7f-151">Przewodnik: Osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="2cd7f-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="2cd7f-152">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd7f-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="2cd7f-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2cd7f-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="2cd7f-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="2cd7f-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [<span data-ttu-id="2cd7f-155">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="2cd7f-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="2cd7f-156">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="2cd7f-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
