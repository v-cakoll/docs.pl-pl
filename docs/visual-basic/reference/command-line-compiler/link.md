---
title: -link
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
ms.openlocfilehash: c15f55f3a3c2b4e404767ddf96e258bc1e9771d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716757"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="6b0d0-102">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b0d0-102">-link (Visual Basic)</span></span>
<span data-ttu-id="6b0d0-103">Powoduje, że kompilator udostępnia informacje o typie COM w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b0d0-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="6b0d0-105">lub</span><span class="sxs-lookup"><span data-stu-id="6b0d0-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b0d0-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6b0d0-106">Arguments</span></span>  
  
|<span data-ttu-id="6b0d0-107">Termin</span><span class="sxs-lookup"><span data-stu-id="6b0d0-107">Term</span></span>|<span data-ttu-id="6b0d0-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="6b0d0-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="6b0d0-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-109">Required.</span></span> <span data-ttu-id="6b0d0-110">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="6b0d0-111">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b0d0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b0d0-112">Remarks</span></span>  
 <span data-ttu-id="6b0d0-113">`-link` Opcja umożliwia wdrożenie aplikacji, która ma informacje o typie osadzonym.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="6b0d0-114">Aplikacja może następnie użyć typów w zestawie środowiska uruchomieniowego, który implementuje informacje o typie osadzonym, bez konieczności odwoływania się do zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="6b0d0-115">Jeśli są publikowane różne wersje zestawu środowiska uruchomieniowego, aplikacja zawierająca informacje o typie osadzonym może współdziałać z różnymi wersjami bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="6b0d0-116">Aby zapoznać się z przykładem, zobacz [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6b0d0-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="6b0d0-117">Korzystanie z `-link` tej opcji jest szczególnie przydatne podczas pracy z międzyoperacyjnym modelem com.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="6b0d0-118">Można osadzić typy COM, aby aplikacja nie wymagała już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="6b0d0-119">`-link` Opcja instruuje kompilator, aby osadzi informacje o typie com z przywoływanego zestawu międzyoperacyjnego do w wyniku skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="6b0d0-120">Typ COM jest identyfikowany przez wartość CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="6b0d0-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="6b0d0-121">W związku z tym aplikacja może działać na komputerze docelowym, na którym zainstalowano te same typy COM z tymi samymi wartościami CLSID.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="6b0d0-122">Aplikacje automatyzujące Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="6b0d0-123">Ponieważ aplikacje, takie jak pakiet Office, zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, których dotyczy odwołanie, tak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a aplikacja korzysta z metod, właściwości lub zdarzeń, które znajdują się w przywoływanych typach COM.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="6b0d0-124">`-link` Opcja osadza tylko interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="6b0d0-125">Osadzanie klas COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b0d0-126">Podczas tworzenia wystąpienia osadzonego typu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="6b0d0-127">Próba utworzenia wystąpienia osadzonego typu COM przy użyciu klasy coclass powoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="6b0d0-128">Aby ustawić `-link` opcję w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` właściwość na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="6b0d0-129">Wartość domyślna dla `Embed Interop Types` właściwości ma **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="6b0d0-130">Jeśli utworzysz link do zestawu COM (zestawu A), który sam odwołuje się do innego zestawu COM (zestawu B), musisz także połączyć się z zestawem B, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="6b0d0-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="6b0d0-131">Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="6b0d0-132">Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="6b0d0-133">Użyj [-LIBPATH](libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="6b0d0-134">Podobnie jak w przypadku opcji kompilatora [odwołania](reference.md) , `-link` opcja kompilatora używa pliku odpowiedzi VBC. rsp, który odwołuje się do często używanych zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="6b0d0-135">Użyj opcji kompilatora [-noconfig](noconfig.md) , jeśli nie chcesz, aby kompilator używał pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="6b0d0-136">Krótka forma `-link` to `-l`.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="6b0d0-137">Typy ogólne i osadzone</span><span class="sxs-lookup"><span data-stu-id="6b0d0-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="6b0d0-138">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="6b0d0-139">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="6b0d0-139">Generic Interfaces</span></span>  
 <span data-ttu-id="6b0d0-140">Nie można użyć ogólnych interfejsów, które są osadzone z zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="6b0d0-141">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="6b0d0-142">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="6b0d0-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="6b0d0-143">Typów, które mają parametr generyczny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć, jeśli ten typ pochodzi z zewnętrznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="6b0d0-144">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="6b0d0-145">Rozważmy na przykład <xref:Microsoft.Office.Interop.Excel.Range> interfejs, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawie.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="6b0d0-146">Jeśli biblioteka osadza typy międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i uwidacznia metodę, która zwraca typ ogólny, który ma parametr, którego typem jest <xref:Microsoft.Office.Interop.Excel.Range> interfejs, ta metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="6b0d0-147">W poniższym przykładzie kod klienta może wywołać metodę, która zwraca interfejs <xref:System.Collections.IList> generyczny bez błędu.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="6b0d0-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b0d0-148">Example</span></span>  
 <span data-ttu-id="6b0d0-149">Poniższy wiersz `OfficeApp.vb` polecenia kompiluje pliki źródłowe i zestawy odwołań z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="6b0d0-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b0d0-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b0d0-150">See also</span></span>

- [<span data-ttu-id="6b0d0-151">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b0d0-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6b0d0-152">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="6b0d0-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="6b0d0-153">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b0d0-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="6b0d0-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6b0d0-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="6b0d0-155">-LIBPATH</span><span class="sxs-lookup"><span data-stu-id="6b0d0-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="6b0d0-156">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="6b0d0-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="6b0d0-157">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="6b0d0-157">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
