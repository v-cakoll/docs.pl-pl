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
ms.openlocfilehash: f1d2c9a1b27032c2f293b876928f581388ed8aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="0d13b-102">Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="0d13b-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="0d13b-103"><xref:System.CodeDom.Compiler> Przestrzeń nazw zawiera interfejsy do generowania kodu źródłowego z wykresów CodeDOM obiektu i zarządzania kompilacji z kompilatorów obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0d13b-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="0d13b-104">Dostawca kodu może wygenerować kodu źródłowego w określonym języku programowania zgodnie z wykresu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="0d13b-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="0d13b-105">Klasa, która pochodzi z <xref:System.CodeDom.Compiler.CodeDomProvider> zwykle zapewnia metody dla Generowanie i kompilowanie kodu dla języka dostawca obsługuje.</span><span class="sxs-lookup"><span data-stu-id="0d13b-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="0d13b-106">Generowanie kodu źródłowego za pomocą dostawcy CodeDOM kodu</span><span class="sxs-lookup"><span data-stu-id="0d13b-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="0d13b-107">Aby wygenerować kod źródłowy w określonym języku, należy wykresu CodeDOM reprezentujący strukturę aby wygenerować kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="0d13b-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="0d13b-108">Poniższy przykład pokazują, jak można utworzyć wystąpienia <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="0d13b-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="0d13b-109">Wykres dla generowania kodu zazwyczaj znajduje się w <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="0d13b-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="0d13b-110">Aby wygenerować kod dla **elementu CodeCompileUnit** zawierający wykresu CodeDOM, należy wywołać <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody dostawcy kodu.</span><span class="sxs-lookup"><span data-stu-id="0d13b-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="0d13b-111">Ta metoda ma parametr <xref:System.IO.TextWriter> używaną do generowania kodu źródłowego, dlatego czasami najpierw utworzyć **TextWriter** mogą być zapisywane na.</span><span class="sxs-lookup"><span data-stu-id="0d13b-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="0d13b-112">W poniższym przykładzie pokazano generowania kodu z **elementu CodeCompileUnit** i pisanie kodu wygenerowanego źródła w pliku o nazwie HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="0d13b-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="0d13b-113">Za pomocą dostawcy CodeDOM kodu do kompilacji zestawy</span><span class="sxs-lookup"><span data-stu-id="0d13b-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="0d13b-114">**Wywoływanie kompilacji**</span><span class="sxs-lookup"><span data-stu-id="0d13b-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="0d13b-115">Aby skompilować zestawu za pomocą dostawcy CodeDom, musi mieć albo kodu źródłowego, aby skompilować w języku, dla którego masz kompilatora lub CodeDOM wykresów tego źródła może generować kod, aby skompilować.</span><span class="sxs-lookup"><span data-stu-id="0d13b-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="0d13b-116">Jeśli kompilacja z wykresu CodeDOM przekazać <xref:System.CodeDom.CodeCompileUnit> zawierający wykres tak, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metody dostawcy kodu.</span><span class="sxs-lookup"><span data-stu-id="0d13b-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="0d13b-117">Jeśli masz pliku kodu źródłowego w języku, który obsługuje usługę kompilator nazwę pliku zawierającego kod źródłowy, aby przekazać <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metody dostawcy CodeDom.</span><span class="sxs-lookup"><span data-stu-id="0d13b-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="0d13b-118">Można również przekazać ciąg zawierający kod źródłowy w języku, który kompilator rozumie, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metody dostawcy CodeDom.</span><span class="sxs-lookup"><span data-stu-id="0d13b-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="0d13b-119">**Konfigurowanie parametrów kompilacji**</span><span class="sxs-lookup"><span data-stu-id="0d13b-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="0d13b-120">Wszystkie standardowe metody wywoływania kompilacji dostawcy CodeDom ma parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> wskazujące opcje, które będą używane dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0d13b-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="0d13b-121">Można określić nazwę pliku dla zestawu wyjściowego w <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> właściwość **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="0d13b-122">W przeciwnym razie będzie używana domyślną nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="0d13b-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="0d13b-123">Domyślnie nowy **CompilerParameters** jest inicjowany z jego <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> ustawioną właściwość **false**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="0d13b-124">Jeśli kompilacja program wykonywalny, należy ustawić **GenerateExecutable** właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="0d13b-125">Gdy **GenerateExecutable** ustawiono **false**, kompilator wygeneruje biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="0d13b-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="0d13b-126">Jeśli kompilacja pliku wykonywalnego z wykresu CodeDOM <xref:System.CodeDom.CodeEntryPointMethod> musi być zdefiniowany na wykresie.</span><span class="sxs-lookup"><span data-stu-id="0d13b-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="0d13b-127">Jeśli istnieje wiele punktów wejścia kodu, może być konieczne ustawić <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> właściwość **CompilerParameters** na nazwę klasy, która określa punkt wejścia do użycia.</span><span class="sxs-lookup"><span data-stu-id="0d13b-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="0d13b-128">Aby uwzględnić informacje o debugowaniu w wygenerowanym pliku wykonywalnego, ustaw <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="0d13b-129">Jeśli projekt odwołuje się do żadnych zestawów, należy określić nazwy zestawu jako elementy w <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> właściwość **CompilerParameters** używany podczas wywoływania kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0d13b-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="0d13b-130">Można utworzyć zestawu, który jest zapisywany w pamięci, a nie na dysku przez ustawienie <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="0d13b-131">Podczas generowania zestawu w pamięci kodu można uzyskać odwołanie do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> właściwość <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="0d13b-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="0d13b-132">Jeśli zestaw jest zapisywany do dysku, można uzyskać ścieżki do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> właściwość **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="0d13b-133">Aby określić argumenty wiersza polecenia niestandardowych ciąg do użycia podczas wywoływania procesu kompilacji, należy określić ciąg <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d13b-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="0d13b-134">Jeśli token zabezpieczający Win32 jest wymagany do wywołania proces kompilatora, określ token w <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d13b-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="0d13b-135">Aby połączyć plik zasobów Win32 w skompilowanym zestawie, określ nazwę pliku zasobów Win32 w <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d13b-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="0d13b-136">Aby określić poziom ostrzeżeń, w którym należy zatrzymać kompilacji, należy ustawić <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> właściwości na liczbę całkowitą reprezentującą poziom ostrzeżenia, na którym zatrzymanie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0d13b-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="0d13b-137">Można również skonfigurować kompilatora zatrzymanie kompilacji, jeśli występują ostrzeżenia przez ustawienie <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="0d13b-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="0d13b-138">Poniższy przykład kodu pokazuje kompilowanie pliku źródłowego przy użyciu dostawcy CodeDom pochodną <xref:System.CodeDom.Compiler.CodeDomProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d13b-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="0d13b-139">Języków z początkową obsługą</span><span class="sxs-lookup"><span data-stu-id="0d13b-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="0d13b-140">.NET Framework zapewnia kompilatory kodu i generatory kodu dla następujących języków: C#, Visual Basic C++ i JScript.</span><span class="sxs-lookup"><span data-stu-id="0d13b-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="0d13b-141">Obsługa codeDOM można rozszerzyć do innych języków zaimplementowanie generatory specyficzny dla języka kodu i kompilatory kodu.</span><span class="sxs-lookup"><span data-stu-id="0d13b-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d13b-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d13b-142">See Also</span></span>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [<span data-ttu-id="0d13b-143">Dynamiczne generowanie i kompilacja kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="0d13b-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [<span data-ttu-id="0d13b-144">Krótki przewodnik codeDOM</span><span class="sxs-lookup"><span data-stu-id="0d13b-144">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
