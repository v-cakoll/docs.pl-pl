---
title: -Link (C# opcje kompilatora)
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
ms.openlocfilehash: ba238a129eddcca606e411a82f04d8da8640bdb2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602819"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="dcbce-102">-Link (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="dcbce-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="dcbce-103">Powoduje, że kompilator udostępnia informacje o typie COM w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcbce-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="dcbce-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dcbce-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="dcbce-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="dcbce-106">Required.</span></span> <span data-ttu-id="dcbce-107">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="dcbce-108">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="dcbce-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcbce-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcbce-109">Remarks</span></span>  
 <span data-ttu-id="dcbce-110">`-link` Opcja umożliwia wdrożenie aplikacji, która ma informacje o typie osadzonym.</span><span class="sxs-lookup"><span data-stu-id="dcbce-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="dcbce-111">Aplikacja może następnie użyć typów w zestawie środowiska uruchomieniowego, który implementuje informacje o typie osadzonym, bez konieczności odwoływania się do zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="dcbce-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="dcbce-112">Jeśli są publikowane różne wersje zestawu środowiska uruchomieniowego, aplikacja zawierająca informacje o typie osadzonym może współdziałać z różnymi wersjami bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="dcbce-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="dcbce-113">Aby zapoznać się z przykładem, zobacz [Przewodnik: Osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="dcbce-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="dcbce-114">Korzystanie z `-link` tej opcji jest szczególnie przydatne podczas pracy z międzyoperacyjnym modelem com.</span><span class="sxs-lookup"><span data-stu-id="dcbce-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="dcbce-115">Można osadzić typy COM, aby aplikacja nie wymagała już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="dcbce-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="dcbce-116">`-link` Opcja instruuje kompilator, aby osadzi informacje o typie com z przywoływanego zestawu międzyoperacyjnego do w wyniku skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="dcbce-117">Typ COM jest identyfikowany przez wartość CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="dcbce-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="dcbce-118">W związku z tym aplikacja może działać na komputerze docelowym, na którym zainstalowano te same typy COM z tymi samymi wartościami CLSID.</span><span class="sxs-lookup"><span data-stu-id="dcbce-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="dcbce-119">Aplikacje automatyzujące Microsoft Office są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="dcbce-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="dcbce-120">Ponieważ aplikacje takie jak pakiet Office zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, których dotyczy odwołanie, tak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a aplikacja korzysta z metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typach COM.</span><span class="sxs-lookup"><span data-stu-id="dcbce-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="dcbce-121">`-link` Opcja osadza tylko interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="dcbce-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="dcbce-122">Osadzanie klas COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dcbce-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcbce-123">Podczas tworzenia wystąpienia osadzonego typu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="dcbce-124">Próba utworzenia wystąpienia osadzonego typu COM przy użyciu klasy coclass powoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="dcbce-125">Aby ustawić `-link` opcję w programie Visual Studio, Dodaj odwołanie do zestawu i `Embed Interop Types` ustaw właściwość na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="dcbce-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="dcbce-126">Wartość domyślna dla `Embed Interop Types` właściwości ma **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="dcbce-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="dcbce-127">Jeśli utworzysz link do zestawu COM (zestawu A), który sam odwołuje się do innego zestawu COM (zestawu B), musisz także połączyć się z zestawem B, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="dcbce-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="dcbce-128">Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="dcbce-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="dcbce-129">Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="dcbce-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="dcbce-130">Podobnie jak w przypadku opcji kompilatora [odwołania](./reference-compiler-option.md) , `-link` opcja kompilatora używa pliku odpowiedzi CSC. rsp, który odwołuje się do często używanych zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dcbce-130">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="dcbce-131">Użyj opcji kompilatora [-noconfig](./noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator używał pliku CSC. rsp.</span><span class="sxs-lookup"><span data-stu-id="dcbce-131">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="dcbce-132">Krótka forma `-link` to `-l`.</span><span class="sxs-lookup"><span data-stu-id="dcbce-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="dcbce-133">Typy ogólne i osadzone</span><span class="sxs-lookup"><span data-stu-id="dcbce-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="dcbce-134">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="dcbce-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="dcbce-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="dcbce-135">Generic Interfaces</span></span>  
 <span data-ttu-id="dcbce-136">Nie można użyć ogólnych interfejsów, które są osadzone z zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dcbce-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="dcbce-137">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dcbce-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="dcbce-138">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="dcbce-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="dcbce-139">Typów, które mają parametr generyczny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć, jeśli ten typ pochodzi z zewnętrznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="dcbce-140">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="dcbce-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="dcbce-141">Rozważmy <xref:Microsoft.Office.Interop.Excel.Range> na przykład interfejs, który jest zdefiniowany <xref:Microsoft.Office.Interop.Excel> w zestawie.</span><span class="sxs-lookup"><span data-stu-id="dcbce-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="dcbce-142">Jeśli biblioteka osadza typy międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i uwidacznia metodę, która zwraca typ ogólny, który ma parametr, którego typem <xref:Microsoft.Office.Interop.Excel.Range> jest interfejs, ta metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="dcbce-143">W poniższym przykładzie kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs generyczny bez błędu.</span><span class="sxs-lookup"><span data-stu-id="dcbce-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="dcbce-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcbce-144">Example</span></span>  
 <span data-ttu-id="dcbce-145">Poniższy `OfficeApp.cs` kod kompiluje pliki źródłowe i zestawy odwołań z `COMData1.dll` i `COMData2.dll` do produkcji. `OfficeApp.exe`</span><span class="sxs-lookup"><span data-stu-id="dcbce-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcbce-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcbce-146">See also</span></span>

- [<span data-ttu-id="dcbce-147">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="dcbce-147">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dcbce-148">Przewodnik: Osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="dcbce-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="dcbce-149">-Reference (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="dcbce-149">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="dcbce-150">-noconfig (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="dcbce-150">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="dcbce-151">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="dcbce-151">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="dcbce-152">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="dcbce-152">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
