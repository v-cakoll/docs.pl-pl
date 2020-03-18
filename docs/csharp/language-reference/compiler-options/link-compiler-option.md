---
title: -link (Opcje kompilatora C#)
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
ms.openlocfilehash: 4c96f7be5ac500886ea036c93b4651fa814ee58a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970110"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="1ae63-102">-link (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1ae63-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="1ae63-103">Powoduje, że kompilator, aby informacje o typie COM w określonych zestawów dostępne dla projektu, który jest obecnie kompilowany.</span><span class="sxs-lookup"><span data-stu-id="1ae63-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ae63-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ae63-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1ae63-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="1ae63-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="1ae63-106">Required.</span></span> <span data-ttu-id="1ae63-107">Lista nazw plików zestawów rozdzielana przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1ae63-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="1ae63-108">Jeśli nazwa pliku zawiera spacja, ujmij nazwę w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="1ae63-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae63-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ae63-109">Remarks</span></span>  
 <span data-ttu-id="1ae63-110">Ta `-link` opcja umożliwia wdrożenie aplikacji, która ma osadzone informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="1ae63-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="1ae63-111">Aplikacja może następnie używać typów w zestawie wykonywania, które implementują informacje o typie osadzonym bez konieczności odwoływania się do zestawu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1ae63-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="1ae63-112">Jeśli zostaną opublikowane różne wersje zestawu w czasie wykonywania, aplikacja zawierająca informacje o typie osadzonym może pracować z różnymi wersjami bez konieczności ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1ae63-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="1ae63-113">Na przykład zobacz [Instruktaż: Osadzanie typów z zestawów zarządzanych](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1ae63-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="1ae63-114">Korzystanie `-link` z tej opcji jest szczególnie przydatne podczas pracy z com interop.</span><span class="sxs-lookup"><span data-stu-id="1ae63-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="1ae63-115">Można osadzać typy COM, tak aby aplikacja nie wymaga już podstawowego zestawu współrzędnego (PIA) na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="1ae63-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="1ae63-116">Opcja `-link` instruuje kompilator, aby osadzić informacje o typie COM z zestawu współdziałania, do którego istnieje odwołanie, do wynikowego skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="1ae63-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="1ae63-117">Typ COM jest identyfikowany przez wartość CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="1ae63-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="1ae63-118">W rezultacie aplikacja może działać na komputerze docelowym, który zainstalował te same typy COM z tymi samymi wartościami IDENTYFIKATORA CLSID.</span><span class="sxs-lookup"><span data-stu-id="1ae63-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="1ae63-119">Dobrym przykładem są aplikacje automatyzujące pakiet Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="1ae63-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="1ae63-120">Ponieważ aplikacje, takie jak Office zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, do których istnieje odwołanie, o ile na komputerze docelowym jest zainstalowany program .NET Framework 4 lub nowszy, a aplikacja korzysta z metod, właściwości lub zdarzenia, które są uwzględnione w typach COM, do których istnieją odwołania.</span><span class="sxs-lookup"><span data-stu-id="1ae63-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="1ae63-121">Opcja `-link` osadza tylko interfejsy, struktury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="1ae63-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="1ae63-122">Osadzanie klas COM nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1ae63-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ae63-123">Podczas tworzenia wystąpienia typu osadzonego COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1ae63-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="1ae63-124">Próba utworzenia wystąpienia typu osadzonego COM przy użyciu coclass powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="1ae63-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="1ae63-125">Aby ustawić `-link` opcję w programie Visual Studio, `Embed Interop Types` dodaj odwołanie do zestawu i ustaw właściwość na **true**.</span><span class="sxs-lookup"><span data-stu-id="1ae63-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="1ae63-126">Wartością domyślną `Embed Interop Types` dla właściwości jest **false**.</span><span class="sxs-lookup"><span data-stu-id="1ae63-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="1ae63-127">Jeśli łączysz się z zestawem COM (złożenie M.In.), który sam odwołuje się do innego zestawu COM (zestawu B), należy również połączyć się z zestawem B, jeśli spełniona jest jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="1ae63-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="1ae63-128">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="1ae63-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="1ae63-129">Pole, właściwość, zdarzenie lub metoda, która ma typ zwracany lub typ parametru z zestawu B jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1ae63-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="1ae63-130">Podobnie jak opcja [kompilatora -reference,](./reference-compiler-option.md) opcja `-link` kompilatora używa pliku odpowiedzi Csc.rsp, który odwołuje się do często używanych zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ae63-130">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="1ae63-131">Użyj opcji [kompilatora -noconfig,](./noconfig-compiler-option.md) jeśli nie chcesz, aby kompilator używał pliku Csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="1ae63-131">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="1ae63-132">Krótka forma `-link` `-l`jest .</span><span class="sxs-lookup"><span data-stu-id="1ae63-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="1ae63-133">Typy ogólne i osadzone</span><span class="sxs-lookup"><span data-stu-id="1ae63-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="1ae63-134">W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy współotora.</span><span class="sxs-lookup"><span data-stu-id="1ae63-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="1ae63-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="1ae63-135">Generic Interfaces</span></span>  
 <span data-ttu-id="1ae63-136">Nie można używać interfejsów ogólnych, które są osadzone z zestawu współdziałania.</span><span class="sxs-lookup"><span data-stu-id="1ae63-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="1ae63-137">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1ae63-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="1ae63-138">Typy, które mają parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="1ae63-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="1ae63-139">Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu współdziałania nie może być używany, jeśli ten typ pochodzi z zestawu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="1ae63-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="1ae63-140">To ograniczenie nie ma zastosowania do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1ae63-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="1ae63-141">Rozważmy na <xref:Microsoft.Office.Interop.Excel.Range> przykład interfejs, który <xref:Microsoft.Office.Interop.Excel> jest zdefiniowany w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1ae63-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="1ae63-142">Jeśli biblioteka osadza typy współdziałania z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ <xref:Microsoft.Office.Interop.Excel.Range> ogólny, który ma parametr, którego typem jest interfejs, ta metoda musi zwrócić ogólny interfejs, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1ae63-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="1ae63-143">W poniższym przykładzie kod klienta można wywołać metodę, która zwraca <xref:System.Collections.IList> ogólny interfejs bez błędów.</span><span class="sxs-lookup"><span data-stu-id="1ae63-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="1ae63-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ae63-144">Example</span></span>  
 <span data-ttu-id="1ae63-145">Poniższy kod kompiluje `OfficeApp.cs` pliki źródłowe `COMData1.dll` `COMData2.dll` i `OfficeApp.exe`zestawy odwołań z i do produkcji .</span><span class="sxs-lookup"><span data-stu-id="1ae63-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ae63-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ae63-146">See also</span></span>

- [<span data-ttu-id="1ae63-147">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="1ae63-147">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1ae63-148">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="1ae63-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="1ae63-149">-reference (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1ae63-149">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="1ae63-150">-noconfig (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1ae63-150">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="1ae63-151">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="1ae63-151">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="1ae63-152">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="1ae63-152">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
