---
title: -link (opcje kompilatora C#)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 049d1ce7a27a812b58fb09802e1ce520e96ed925
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586021"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="62e5b-102">-link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="62e5b-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="62e5b-103">Powoduje, że kompilator udostępnia informacje o typie modelu COM w określonych zestawach do projektu, który obecnie kompilacja.</span><span class="sxs-lookup"><span data-stu-id="62e5b-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e5b-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="62e5b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="62e5b-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="62e5b-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="62e5b-106">Required.</span></span> <span data-ttu-id="62e5b-107">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="62e5b-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="62e5b-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="62e5b-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62e5b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e5b-109">Remarks</span></span>  
 <span data-ttu-id="62e5b-110">`-link` Opcja służy do wdrażania aplikacji, która zawiera osadzone informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="62e5b-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="62e5b-111">Aplikacja następnie można użyć typów w zestawie środowiska uruchomieniowego, które implementują informacje o typie osadzony bez odwołania do zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="62e5b-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="62e5b-112">Jeśli różne wersje zestawów środowiska uruchomieniowego są publikowane, aplikacji, która zawiera informacje o typie osadzony pracować z różnymi wersjami bez konieczności zostać zrekompilowane.</span><span class="sxs-lookup"><span data-stu-id="62e5b-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="62e5b-113">Aby uzyskać przykład, zobacz [instruktażu: Osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="62e5b-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="62e5b-114">Za pomocą `-link` opcja jest szczególnie przydatna w przypadku, gdy pracujesz za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="62e5b-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="62e5b-115">Można osadzić typów modelu COM, dzięki czemu aplikacja nie wymaga już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="62e5b-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="62e5b-116">`-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie modelu COM z odwołania zestawu międzyoperacyjnego wynikowy kod skompilowany.</span><span class="sxs-lookup"><span data-stu-id="62e5b-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="62e5b-117">Typ COM jest identyfikowany przez wartość identyfikatora CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="62e5b-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="62e5b-118">W rezultacie aplikację można uruchomić na komputerze docelowym, w której zainstalowano te same typy modelu COM za pomocą tych samych wartości identyfikatora CLSID.</span><span class="sxs-lookup"><span data-stu-id="62e5b-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="62e5b-119">Aplikacje, które automatyzują Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="62e5b-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="62e5b-120">Ponieważ aplikacji, takich jak Office zwykle zachować tę samą wartość identyfikatora CLSID różnych wersji, aplikacja może używać typów modelu COM, jak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a Twoja aplikacja używa metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="62e5b-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="62e5b-121">`-link` Opcja osadza interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="62e5b-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="62e5b-122">Osadzanie klasy COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="62e5b-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62e5b-123">Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="62e5b-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="62e5b-124">Próba utworzenia wystąpienia typu osadzonego modelu COM za pomocą wspólna spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="62e5b-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="62e5b-125">Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="62e5b-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="62e5b-126">Wartość domyślna dla `Embed Interop Types` właściwość **false**.</span><span class="sxs-lookup"><span data-stu-id="62e5b-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="62e5b-127">Jeśli łączysz się do zestawu COM (Assembly A) która sama odwołuje się do innego zestawu modelu COM (Assembly B), musisz również link do zestawu B, jeśli jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="62e5b-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="62e5b-128">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="62e5b-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="62e5b-129">Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="62e5b-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="62e5b-130">Podobnie jak [— dokumentacja](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora, `-link` — opcja kompilatora używa pliku Csc.rsp odpowiedzi, która odwołuje się do często używanych zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62e5b-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="62e5b-131">Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) opcji kompilatora, jeśli nie chcesz, aby kompilator, aby użyć pliku Csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="62e5b-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="62e5b-132">Krótkiej formy `-link` jest `-l`.</span><span class="sxs-lookup"><span data-stu-id="62e5b-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="62e5b-133">Typy ogólne i osadzone typy</span><span class="sxs-lookup"><span data-stu-id="62e5b-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="62e5b-134">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="62e5b-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="62e5b-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="62e5b-135">Generic Interfaces</span></span>  
 <span data-ttu-id="62e5b-136">Nie można używać interfejsów ogólnych, które są osadzone w zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="62e5b-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="62e5b-137">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="62e5b-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="62e5b-138">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="62e5b-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="62e5b-139">Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zestawu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="62e5b-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="62e5b-140">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="62e5b-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="62e5b-141">Na przykład, rozważmy <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="62e5b-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="62e5b-142">Jeśli biblioteka osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ ogólny, który ma parametr, którego typ jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu i metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="62e5b-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="62e5b-143">W poniższym przykładzie, kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs ogólny bez błędów.</span><span class="sxs-lookup"><span data-stu-id="62e5b-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="62e5b-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="62e5b-144">Example</span></span>  
 <span data-ttu-id="62e5b-145">Poniższy kod kompiluje plik źródłowy `OfficeApp.cs` i odwoływać się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="62e5b-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="62e5b-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62e5b-146">See also</span></span>

- [<span data-ttu-id="62e5b-147">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="62e5b-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="62e5b-148">Przewodnik: Osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="62e5b-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="62e5b-149">— Odwołanie (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="62e5b-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
- [<span data-ttu-id="62e5b-150">-noconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="62e5b-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)
- [<span data-ttu-id="62e5b-151">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="62e5b-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="62e5b-152">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="62e5b-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
