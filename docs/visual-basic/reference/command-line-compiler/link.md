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
ms.openlocfilehash: 0a6a6b6436210e699d8fd176dc1ba6e4aded7c8d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523978"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="c1a4f-102">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1a4f-102">-link (Visual Basic)</span></span>
<span data-ttu-id="c1a4f-103">Powoduje, że kompilator udostępnia informacje o typie COM w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1a4f-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="c1a4f-105">lub</span><span class="sxs-lookup"><span data-stu-id="c1a4f-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1a4f-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c1a4f-106">Arguments</span></span>  
  
|<span data-ttu-id="c1a4f-107">Termin</span><span class="sxs-lookup"><span data-stu-id="c1a4f-107">Term</span></span>|<span data-ttu-id="c1a4f-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="c1a4f-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="c1a4f-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-109">Required.</span></span> <span data-ttu-id="c1a4f-110">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="c1a4f-111">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a4f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1a4f-112">Remarks</span></span>  
 <span data-ttu-id="c1a4f-113">Opcja `-link` umożliwia wdrożenie aplikacji, która ma informacje o typie osadzonym.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="c1a4f-114">Aplikacja może następnie użyć typów w zestawie środowiska uruchomieniowego, który implementuje informacje o typie osadzonym, bez konieczności odwoływania się do zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="c1a4f-115">Jeśli są publikowane różne wersje zestawu środowiska uruchomieniowego, aplikacja zawierająca informacje o typie osadzonym może współdziałać z różnymi wersjami bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="c1a4f-116">Aby zapoznać się z przykładem, zobacz [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c1a4f-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="c1a4f-117">Użycie opcji `-link` jest szczególnie przydatne podczas pracy z międzyoperacyjną obsługą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="c1a4f-118">Można osadzić typy COM, aby aplikacja nie wymagała już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="c1a4f-119">Opcja `-link` instruuje kompilator, aby osadzi informacje o typie COM z przywoływanego zestawu międzyoperacyjnego do w wyniku skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="c1a4f-120">Typ COM jest identyfikowany przez wartość CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="c1a4f-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="c1a4f-121">W związku z tym aplikacja może działać na komputerze docelowym, na którym zainstalowano te same typy COM z tymi samymi wartościami CLSID.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="c1a4f-122">Aplikacje automatyzujące Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="c1a4f-123">Ponieważ aplikacje takie jak pakiet Office zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, których dotyczy odwołanie, tak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a aplikacja korzysta z metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typach COM.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="c1a4f-124">Opcja `-link` umożliwia osadzanie tylko interfejsów, struktur i delegatów.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="c1a4f-125">Osadzanie klas COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1a4f-126">Podczas tworzenia wystąpienia osadzonego typu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="c1a4f-127">Próba utworzenia wystąpienia osadzonego typu COM przy użyciu klasy coclass powoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="c1a4f-128">Aby ustawić opcję `-link` w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw właściwość `Embed Interop Types` na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="c1a4f-129">Wartością domyślną dla właściwości `Embed Interop Types` jest **false**.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="c1a4f-130">Jeśli utworzysz link do zestawu COM (zestawu A), który sam odwołuje się do innego zestawu COM (zestawu B), musisz także połączyć się z zestawem B, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="c1a4f-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="c1a4f-131">Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="c1a4f-132">Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="c1a4f-133">Użyj [-LIBPATH](libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="c1a4f-134">Podobnie jak w przypadku opcji kompilatora [referencyjnego](reference.md) , opcja kompilatora `-link` używa pliku odpowiedzi VBC. rsp, który odwołuje się do często używanych .NET Framework zestawów.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="c1a4f-135">Użyj opcji kompilatora [-noconfig](noconfig.md) , jeśli nie chcesz, aby kompilator używał pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="c1a4f-136">Krótka forma `-link` jest `-l`.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="c1a4f-137">Typy ogólne i osadzone</span><span class="sxs-lookup"><span data-stu-id="c1a4f-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="c1a4f-138">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="c1a4f-139">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="c1a4f-139">Generic Interfaces</span></span>  
 <span data-ttu-id="c1a4f-140">Nie można użyć ogólnych interfejsów, które są osadzone z zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="c1a4f-141">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="c1a4f-142">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="c1a4f-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="c1a4f-143">Typów, które mają parametr generyczny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć, jeśli ten typ pochodzi z zewnętrznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="c1a4f-144">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="c1a4f-145">Rozważmy na przykład interfejs <xref:Microsoft.Office.Interop.Excel.Range>, który jest zdefiniowany w zestawie <xref:Microsoft.Office.Interop.Excel>.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="c1a4f-146">Jeśli biblioteka osadza typy międzyoperacyjnych z zestawu <xref:Microsoft.Office.Interop.Excel> i uwidacznia metodę zwracającą typ ogólny, który ma parametr, którego typem jest interfejs <xref:Microsoft.Office.Interop.Excel.Range>, ta metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="c1a4f-147">W poniższym przykładzie kod klienta może wywołać metodę, która zwraca interfejs ogólny <xref:System.Collections.IList> bez błędu.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="c1a4f-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1a4f-148">Example</span></span>  
 <span data-ttu-id="c1a4f-149">Poniższy wiersz polecenia kompiluje plik źródłowy `OfficeApp.vb` i zestawów referencyjnych z `COMData1.dll` i `COMData2.dll`, aby utworzyć `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="c1a4f-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1a4f-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1a4f-150">See also</span></span>

- [<span data-ttu-id="c1a4f-151">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1a4f-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c1a4f-152">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="c1a4f-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="c1a4f-153">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1a4f-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="c1a4f-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="c1a4f-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="c1a4f-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="c1a4f-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="c1a4f-156">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c1a4f-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="c1a4f-157">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="c1a4f-157">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
