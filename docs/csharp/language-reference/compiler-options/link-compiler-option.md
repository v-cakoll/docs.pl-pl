---
title: -link (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 12ba3762a1c514c52b844a30efc9f49648c51b46
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="95cfa-102">-link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="95cfa-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="95cfa-103">Powoduje, że kompilator, aby udostępnić informacje o typie modelu COM w określonych zestawów do projektu, które są aktualnie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="95cfa-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95cfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95cfa-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="95cfa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="95cfa-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="95cfa-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="95cfa-106">Required.</span></span> <span data-ttu-id="95cfa-107">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="95cfa-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="95cfa-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="95cfa-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95cfa-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95cfa-109">Remarks</span></span>  
 <span data-ttu-id="95cfa-110">`-link` Opcja umożliwia wdrażanie aplikacji, która zawiera osadzone informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="95cfa-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="95cfa-111">Aplikacja może następnie używać typów w zestawie środowiska uruchomieniowego, które implementują informacji osadzonym typem bez konieczności odwołanie do zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="95cfa-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="95cfa-112">Jeśli w różnych wersjach zestawu środowiska wykonawczego są publikowane, aplikacji, który zawiera informacje o osadzonym typem może współpracować z różnych wersji bez konieczności ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="95cfa-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="95cfa-113">Na przykład zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="95cfa-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="95cfa-114">Przy użyciu `-link` opcja jest szczególnie przydatne podczas pracy z COM interop.</span><span class="sxs-lookup"><span data-stu-id="95cfa-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="95cfa-115">Można osadzić typów COM, aby aplikacja nie wymaga już podstawowy zestaw międzyoperacyjny (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="95cfa-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="95cfa-116">`-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie COM z przywoływanego zestawu międzyoperacyjnego na wynikowej skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="95cfa-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="95cfa-117">Typ modelu COM jest identyfikowany przez wartość identyfikatora CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="95cfa-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="95cfa-118">W związku z tym aplikację można uruchomić na komputerze docelowym, który zainstalował takich samych typach modelu COM przy użyciu tej samej wartości identyfikatora CLSID.</span><span class="sxs-lookup"><span data-stu-id="95cfa-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="95cfa-119">Dobrym przykładem są aplikacje, które automatyzują Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="95cfa-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="95cfa-120">Ponieważ aplikacji, takich jak Office zazwyczaj zachować taką samą wartość identyfikatora CLSID w różnych wersjach, aplikacja może używać wskazanych typów COM, jak długo jako .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym i aplikacja korzysta z metod, właściwości lub zdarzenia, które są objęte wskazanych typów COM.</span><span class="sxs-lookup"><span data-stu-id="95cfa-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="95cfa-121">`-link` Opcja osadza interfejsów, struktur i delegatów.</span><span class="sxs-lookup"><span data-stu-id="95cfa-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="95cfa-122">Osadzanie klasy COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="95cfa-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95cfa-123">Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95cfa-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="95cfa-124">Podjęto próbę utworzenia wystąpienia typu osadzonego modelu COM za pomocą klasy CoClass powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="95cfa-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="95cfa-125">Aby ustawić `-link` opcji w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], Dodaj odwołanie do zestawu danych i ustaw `Embed Interop Types` właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="95cfa-125">To set the `-link` option in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="95cfa-126">Wartość domyślna dla `Embed Interop Types` właściwość jest **false**.</span><span class="sxs-lookup"><span data-stu-id="95cfa-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="95cfa-127">Gdy łącze do zestawu COM (zestaw A) które odwołuje się do innego zestawu COM (zestaw B), należy także łącze do zestawu B, jeśli spełniony jest jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="95cfa-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="95cfa-128">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="95cfa-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="95cfa-129">Pola, właściwości, zdarzenia lub metodę, która ma zwracany typ lub parametr typu z B zestawu jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="95cfa-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="95cfa-130">Podobnie jak [— odwołanie](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora, `-link` — opcja kompilatora używa Csc.rsp plik odpowiedzi, który odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="95cfa-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="95cfa-131">Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) opcję kompilatora, jeśli nie chcesz kompilatora, aby użyć pliku Csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="95cfa-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="95cfa-132">Krótka forma z `-link` jest `-l`.</span><span class="sxs-lookup"><span data-stu-id="95cfa-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="95cfa-133">Typy ogólne i osadzone typy</span><span class="sxs-lookup"><span data-stu-id="95cfa-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="95cfa-134">W poniższych sekcjach opisano ograniczenia przy użyciu typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="95cfa-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="95cfa-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="95cfa-135">Generic Interfaces</span></span>  
 <span data-ttu-id="95cfa-136">Nie można używać interfejsów ogólnych osadzonych z zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="95cfa-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="95cfa-137">Przedstawiono to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="95cfa-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="95cfa-138">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="95cfa-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="95cfa-139">Typy, które mają parametru ogólnego, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zewnętrznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="95cfa-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="95cfa-140">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="95cfa-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="95cfa-141">Rozważmy na przykład <xref:Microsoft.Office.Interop.Excel.Range> interfejs, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="95cfa-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="95cfa-142">Jeśli biblioteki osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca wartość typu ogólnego, który ma parametr typu jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="95cfa-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 <span data-ttu-id="95cfa-143">W poniższym przykładzie kodu klienta można wywołać metodę, która zwraca <xref:System.Collections.IList> ogólny interfejs bez błędów.</span><span class="sxs-lookup"><span data-stu-id="95cfa-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="95cfa-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="95cfa-144">Example</span></span>  
 <span data-ttu-id="95cfa-145">Poniższy kod tworzy plik źródłowy `OfficeApp.cs` i odwołuje się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="95cfa-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="95cfa-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95cfa-146">See Also</span></span>  
 [<span data-ttu-id="95cfa-147">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="95cfa-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="95cfa-148">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="95cfa-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="95cfa-149">— Odwołanie (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="95cfa-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [<span data-ttu-id="95cfa-150">-noconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="95cfa-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [<span data-ttu-id="95cfa-151">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="95cfa-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="95cfa-152">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="95cfa-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
