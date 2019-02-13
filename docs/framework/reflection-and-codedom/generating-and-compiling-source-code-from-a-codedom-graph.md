---
title: Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0218f74f5aa66921104fd36c085aaed04c9b435
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219528"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="83f30-102">Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="83f30-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="83f30-103"><xref:System.CodeDom.Compiler> Przestrzeń nazw zawiera interfejsy do generowania kodu źródłowego z wykresu obiektu CodeDOM i zarządzania kompilacji za pomocą obsługiwane kompilatory.</span><span class="sxs-lookup"><span data-stu-id="83f30-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="83f30-104">Dostawcy kodu może wygenerować kod źródłowy w języku programowania określonym zgodnie z wykresu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="83f30-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="83f30-105">Klasa, która pochodzi od klasy <xref:System.CodeDom.Compiler.CodeDomProvider> zazwyczaj może zapewnić metody dla Generowanie i kompilowanie kodu dla języka dostawca obsługuje.</span><span class="sxs-lookup"><span data-stu-id="83f30-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="83f30-106">Za pomocą dostawcy kodu CodeDOM, aby wygenerować kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="83f30-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="83f30-107">Aby wygenerować kod źródłowy w określonym języku, należy wykresu CodeDOM, który reprezentuje strukturę kodu źródłowego do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="83f30-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="83f30-108">Poniższy przykład pokazuje, jak utworzyć wystąpienie <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="83f30-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="83f30-109">Wykres dla generowania kodu jest zwykle są zawarte w <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="83f30-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="83f30-110">Aby wygenerować kod dla **elementu CodeCompileUnit** zawierającą wykresu CodeDOM, wywołaj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody dostawcy kodu.</span><span class="sxs-lookup"><span data-stu-id="83f30-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="83f30-111">Ta metoda ma parametr <xref:System.IO.TextWriter> używaną do generowania kodu źródłowego, więc czasami trzeba najpierw utworzyć **TextWriter** , mogą być zapisywane.</span><span class="sxs-lookup"><span data-stu-id="83f30-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="83f30-112">W poniższym przykładzie pokazano generowanie kodu z **elementu CodeCompileUnit** i pisanie kodu wygenerowanego źródła w pliku o nazwie HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="83f30-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="83f30-113">Kompilowanie zestawów przy użyciu dostawcy kodu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="83f30-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="83f30-114">**Wywoływanie kompilacji**</span><span class="sxs-lookup"><span data-stu-id="83f30-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="83f30-115">Aby skompilować zestawu przy użyciu dostawcy CodeDom, musi być albo kod źródłowy do skompilowania w języku, do której masz kompilatora lub modelu CodeDOM wykresu tego źródła kodu, aby skompilować mogą być generowane z.</span><span class="sxs-lookup"><span data-stu-id="83f30-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="83f30-116">Jeśli kompilujesz z wykresu CodeDOM, przekazać <xref:System.CodeDom.CodeCompileUnit> zawierający wykres, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metody dostawcy kodu.</span><span class="sxs-lookup"><span data-stu-id="83f30-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="83f30-117">Jeśli masz plik kodu źródłowego w języku, który kompilator rozpoznaje, przekazać nazwę pliku zawierającego kod źródłowy w celu <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metody dostawcy CodeDom.</span><span class="sxs-lookup"><span data-stu-id="83f30-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="83f30-118">Można również przekazać ciąg zawierający kod źródłowy w języku, który rozumie kompilator, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metody dostawcy CodeDom.</span><span class="sxs-lookup"><span data-stu-id="83f30-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="83f30-119">**Konfigurowanie parametrów kompilacji**</span><span class="sxs-lookup"><span data-stu-id="83f30-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="83f30-120">Wszystkie standardowe metody wywoływania kompilacji dostawcy CodeDom ma parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> oznacza to, opcje, które będą używane dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="83f30-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="83f30-121">Można określić nazwę pliku dla zestawu wyjściowego w <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> właściwość **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="83f30-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="83f30-122">W przeciwnym razie posłuży domyślną nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="83f30-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="83f30-123">Domyślnie nowy **CompilerParameters** jest inicjowany za pomocą jego <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> właściwością **false**.</span><span class="sxs-lookup"><span data-stu-id="83f30-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="83f30-124">Jeśli kompilujesz program wykonywalny, musisz ustawić **GenerateExecutable** właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="83f30-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="83f30-125">Gdy **GenerateExecutable** ustawiono **false**, kompilator wygeneruje bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="83f30-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="83f30-126">Jeśli kompilacja pliku wykonywalnego z wykresu CodeDOM <xref:System.CodeDom.CodeEntryPointMethod> muszą być zdefiniowane na wykresie.</span><span class="sxs-lookup"><span data-stu-id="83f30-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="83f30-127">Jeśli istnieje wiele punktów wejścia kodu, może być konieczne Ustawianie <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> właściwość **CompilerParameters** na nazwę klasy, która definiuje punkt wejścia do użycia.</span><span class="sxs-lookup"><span data-stu-id="83f30-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="83f30-128">Aby dołączyć informacje o debugowaniu wygenerowany plik wykonywalny, należy ustawić <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="83f30-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="83f30-129">Jeśli projekt odwołuje się do wszystkich zestawów, należy określić nazwy zestawu jako elementy <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> właściwość **CompilerParameters** użycia podczas wywoływania kompilacji.</span><span class="sxs-lookup"><span data-stu-id="83f30-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="83f30-130">Można też kompilować zestaw, który jest zapisywany w pamięci, a nie na dysku, ustawiając <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="83f30-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="83f30-131">Podczas generowania zestawu w pamięci, Twój kod może uzyskać odwołanie do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> właściwość <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="83f30-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="83f30-132">Jeśli zestaw został napisany na dysku, można uzyskać ścieżki do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> właściwość **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="83f30-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="83f30-133">Aby określić ciąg niestandardowe argumenty wiersza polecenia do użycia podczas wywoływania procesu kompilacji, należy określić ciąg <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="83f30-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="83f30-134">W przypadku systemu Win32 token zabezpieczający jest wymagany do wywołania proces kompilatora, należy określić token w <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="83f30-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="83f30-135">Aby połączyć pliku zasobów Win32 w skompilowanym zestawie, określ nazwę pliku zasobów Win32 w <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="83f30-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="83f30-136">Aby określić poziom ostrzeżeń, od którego należy zatrzymać kompilacji, ustaw <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> właściwości na liczbę całkowitą reprezentującą poziom ostrzeżeń, od którego należy zatrzymać kompilację.</span><span class="sxs-lookup"><span data-stu-id="83f30-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="83f30-137">Można również skonfigurować kompilator, aby zatrzymać kompilacji, jeśli nie zostaną napotkane ostrzeżenia, ustawiając <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="83f30-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="83f30-138">Poniższy przykład kodu demonstruje, kompilowanie pliku źródłowego, za pomocą dostawcy CodeDom pochodną <xref:System.CodeDom.Compiler.CodeDomProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="83f30-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="83f30-139">Języków z początkową obsługą</span><span class="sxs-lookup"><span data-stu-id="83f30-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="83f30-140">Program .NET Framework oferuje kompilatory kodu i generatorów kodu w następujących językach: C#, Visual Basic, C++ i JScript.</span><span class="sxs-lookup"><span data-stu-id="83f30-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="83f30-141">Obsługa codeDOM można rozszerzyć do innych języków, implementowanie generatorów kodu specyficznego dla języka i kompilatory kodu.</span><span class="sxs-lookup"><span data-stu-id="83f30-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f30-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83f30-142">See also</span></span>
- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="83f30-143">Dynamiczne generowanie i kompilacja kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="83f30-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="83f30-144">[CodeDOM — podręczny wykaz](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83f30-144">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
