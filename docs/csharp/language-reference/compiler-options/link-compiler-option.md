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
ms.openlocfilehash: 00cfda489feb468c7e3c140ab63369b408b09152
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710862"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="2016f-102">-link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2016f-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="2016f-103">Powoduje, że kompilator udostępnia informacje o typie modelu COM w określonych zestawach do projektu, który obecnie kompilacja.</span><span class="sxs-lookup"><span data-stu-id="2016f-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2016f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2016f-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2016f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2016f-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="2016f-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2016f-106">Required.</span></span> <span data-ttu-id="2016f-107">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="2016f-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2016f-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="2016f-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2016f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2016f-109">Remarks</span></span>  
 <span data-ttu-id="2016f-110">`-link` Opcja służy do wdrażania aplikacji, która zawiera osadzone informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="2016f-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="2016f-111">Aplikacja następnie można użyć typów w zestawie środowiska uruchomieniowego, które implementują informacje o typie osadzony bez odwołania do zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2016f-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="2016f-112">Jeśli różne wersje zestawów środowiska uruchomieniowego są publikowane, aplikacji, która zawiera informacje o typie osadzony pracować z różnymi wersjami bez konieczności zostać zrekompilowane.</span><span class="sxs-lookup"><span data-stu-id="2016f-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="2016f-113">Aby uzyskać przykład, zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2016f-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="2016f-114">Za pomocą `-link` opcja jest szczególnie przydatna w przypadku, gdy pracujesz za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2016f-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="2016f-115">Można osadzić typów modelu COM, dzięki czemu aplikacja nie wymaga już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="2016f-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="2016f-116">`-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie modelu COM z odwołania zestawu międzyoperacyjnego wynikowy kod skompilowany.</span><span class="sxs-lookup"><span data-stu-id="2016f-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="2016f-117">Typ COM jest identyfikowany przez wartość identyfikatora CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="2016f-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="2016f-118">W rezultacie aplikację można uruchomić na komputerze docelowym, w której zainstalowano te same typy modelu COM za pomocą tych samych wartości identyfikatora CLSID.</span><span class="sxs-lookup"><span data-stu-id="2016f-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="2016f-119">Aplikacje, które automatyzują Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="2016f-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="2016f-120">Ponieważ aplikacji, takich jak Office zwykle zachować tę samą wartość identyfikatora CLSID różnych wersji, aplikacja może używać typów modelu COM, jak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a Twoja aplikacja używa metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2016f-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="2016f-121">`-link` Opcja osadza interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="2016f-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="2016f-122">Osadzanie klasy COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2016f-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2016f-123">Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2016f-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="2016f-124">Próba utworzenia wystąpienia typu osadzonego modelu COM za pomocą wspólna spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="2016f-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="2016f-125">Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="2016f-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="2016f-126">Wartość domyślna dla `Embed Interop Types` właściwość **false**.</span><span class="sxs-lookup"><span data-stu-id="2016f-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="2016f-127">Jeśli łączysz się do zestawu COM (Assembly A) która sama odwołuje się do innego zestawu modelu COM (Assembly B), musisz również link do zestawu B, jeśli jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2016f-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="2016f-128">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="2016f-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="2016f-129">Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="2016f-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2016f-130">Podobnie jak [— odwołanie](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora, `-link` — opcja kompilatora korzysta z pliku odpowiedzi Csc.rsp odwołania często używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="2016f-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="2016f-131">Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) opcji kompilatora, jeśli nie chcesz, aby kompilator, aby użyć pliku Csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="2016f-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="2016f-132">Krótkiej formy `-link` jest `-l`.</span><span class="sxs-lookup"><span data-stu-id="2016f-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="2016f-133">Typy ogólne i osadzone typy</span><span class="sxs-lookup"><span data-stu-id="2016f-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="2016f-134">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="2016f-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="2016f-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="2016f-135">Generic Interfaces</span></span>  
 <span data-ttu-id="2016f-136">Nie można używać interfejsów ogólnych, które są osadzone w zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="2016f-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="2016f-137">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2016f-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="2016f-138">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="2016f-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="2016f-139">Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zestawu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="2016f-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="2016f-140">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2016f-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="2016f-141">Na przykład, rozważmy <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="2016f-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="2016f-142">Jeśli biblioteka osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ ogólny, który ma parametr, którego typ jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu i metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2016f-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 <span data-ttu-id="2016f-143">W poniższym przykładzie, kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs ogólny bez błędów.</span><span class="sxs-lookup"><span data-stu-id="2016f-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="2016f-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="2016f-144">Example</span></span>  
 <span data-ttu-id="2016f-145">Poniższy kod kompiluje plik źródłowy `OfficeApp.cs` i odwoływać się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="2016f-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2016f-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2016f-146">See Also</span></span>

- [<span data-ttu-id="2016f-147">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="2016f-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="2016f-148">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="2016f-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [<span data-ttu-id="2016f-149">— Odwołanie (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2016f-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
- [<span data-ttu-id="2016f-150">-noconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2016f-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
- [<span data-ttu-id="2016f-151">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="2016f-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="2016f-152">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="2016f-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
