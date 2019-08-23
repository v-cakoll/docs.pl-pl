---
title: -Link (Visual Basic)
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
ms.openlocfilehash: fbce22755b3732896a226c00bbf8e068dc1f098e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929394"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="73a9b-102">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a9b-102">-link (Visual Basic)</span></span>
<span data-ttu-id="73a9b-103">Powoduje, że kompilator udostępnia informacje o typie COM w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73a9b-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="73a9b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="73a9b-105">Arguments</span></span>  
  
|<span data-ttu-id="73a9b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="73a9b-106">Term</span></span>|<span data-ttu-id="73a9b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="73a9b-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="73a9b-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="73a9b-108">Required.</span></span> <span data-ttu-id="73a9b-109">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="73a9b-110">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="73a9b-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73a9b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73a9b-111">Remarks</span></span>  
 <span data-ttu-id="73a9b-112">`-link` Opcja umożliwia wdrożenie aplikacji, która ma informacje o typie osadzonym.</span><span class="sxs-lookup"><span data-stu-id="73a9b-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="73a9b-113">Aplikacja może następnie użyć typów w zestawie środowiska uruchomieniowego, który implementuje informacje o typie osadzonym, bez konieczności odwoływania się do zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="73a9b-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="73a9b-114">Jeśli są publikowane różne wersje zestawu środowiska uruchomieniowego, aplikacja zawierająca informacje o typie osadzonym może współdziałać z różnymi wersjami bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="73a9b-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="73a9b-115">Aby zapoznać się z przykładem, zobacz [Przewodnik: Osadzanie typów z zarządzanych zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="73a9b-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>  
  
 <span data-ttu-id="73a9b-116">Korzystanie z `-link` tej opcji jest szczególnie przydatne podczas pracy z międzyoperacyjnym modelem com.</span><span class="sxs-lookup"><span data-stu-id="73a9b-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="73a9b-117">Można osadzić typy COM, aby aplikacja nie wymagała już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="73a9b-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="73a9b-118">`-link` Opcja instruuje kompilator, aby osadzi informacje o typie com z przywoływanego zestawu międzyoperacyjnego do w wyniku skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="73a9b-119">Typ COM jest identyfikowany przez wartość CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="73a9b-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="73a9b-120">W związku z tym aplikacja może działać na komputerze docelowym, na którym zainstalowano te same typy COM z tymi samymi wartościami CLSID.</span><span class="sxs-lookup"><span data-stu-id="73a9b-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="73a9b-121">Aplikacje automatyzujące Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="73a9b-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="73a9b-122">Ponieważ aplikacje takie jak pakiet Office zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, których dotyczy odwołanie, tak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a aplikacja korzysta z metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typach COM.</span><span class="sxs-lookup"><span data-stu-id="73a9b-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="73a9b-123">`-link` Opcja osadza tylko interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="73a9b-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="73a9b-124">Osadzanie klas COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="73a9b-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73a9b-125">Podczas tworzenia wystąpienia osadzonego typu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="73a9b-126">Próba utworzenia wystąpienia osadzonego typu COM przy użyciu klasy coclass powoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="73a9b-127">Aby ustawić `-link` opcję w programie Visual Studio, Dodaj odwołanie do zestawu i `Embed Interop Types` ustaw właściwość na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="73a9b-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="73a9b-128">Wartość domyślna dla `Embed Interop Types` właściwości ma **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="73a9b-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="73a9b-129">Jeśli utworzysz link do zestawu COM (zestawu A), który sam odwołuje się do innego zestawu COM (zestawu B), musisz także połączyć się z zestawem B, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="73a9b-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="73a9b-130">Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="73a9b-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="73a9b-131">Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="73a9b-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="73a9b-132">Użyj [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="73a9b-133">Podobnie jak [](../../../visual-basic/reference/command-line-compiler/reference.md) w przypadku opcji kompilatora/Reference `-link` , opcja kompilatora używa pliku odpowiedzi VBC. rsp, który odwołuje się do często używanych zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73a9b-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="73a9b-134">Użyj opcji kompilatora [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) , jeśli nie chcesz, aby kompilator używał pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="73a9b-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="73a9b-135">Krótka forma `-link` to `-l`.</span><span class="sxs-lookup"><span data-stu-id="73a9b-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="73a9b-136">Typy ogólne i osadzone</span><span class="sxs-lookup"><span data-stu-id="73a9b-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="73a9b-137">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="73a9b-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="73a9b-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="73a9b-138">Generic Interfaces</span></span>  
 <span data-ttu-id="73a9b-139">Nie można użyć ogólnych interfejsów, które są osadzone z zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="73a9b-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="73a9b-140">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="73a9b-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="73a9b-141">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="73a9b-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="73a9b-142">Typów, które mają parametr generyczny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć, jeśli ten typ pochodzi z zewnętrznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="73a9b-143">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="73a9b-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="73a9b-144">Rozważmy <xref:Microsoft.Office.Interop.Excel.Range> na przykład interfejs, który jest zdefiniowany <xref:Microsoft.Office.Interop.Excel> w zestawie.</span><span class="sxs-lookup"><span data-stu-id="73a9b-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="73a9b-145">Jeśli biblioteka osadza typy międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i uwidacznia metodę, która zwraca typ ogólny, który ma parametr, którego typem <xref:Microsoft.Office.Interop.Excel.Range> jest interfejs, ta metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="73a9b-146">W poniższym przykładzie kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs generyczny bez błędu.</span><span class="sxs-lookup"><span data-stu-id="73a9b-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="73a9b-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="73a9b-147">Example</span></span>  
 <span data-ttu-id="73a9b-148">Poniższy wiersz polecenia `OfficeApp.vb` kompiluje pliki źródłowe i zestawy odwołań z `COMData1.dll` i `COMData2.dll` do produkcji. `OfficeApp.exe`</span><span class="sxs-lookup"><span data-stu-id="73a9b-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="73a9b-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73a9b-149">See also</span></span>

- [<span data-ttu-id="73a9b-150">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73a9b-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="73a9b-151">Przewodnik: Osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="73a9b-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="73a9b-152">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a9b-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="73a9b-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="73a9b-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="73a9b-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="73a9b-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [<span data-ttu-id="73a9b-155">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="73a9b-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="73a9b-156">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="73a9b-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
