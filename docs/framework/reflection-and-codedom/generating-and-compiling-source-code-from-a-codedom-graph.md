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
ms.openlocfilehash: a8d3bf7363cb887834a1c251aead05c75e2e3fe8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130219"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM
Przestrzeń nazw <xref:System.CodeDom.Compiler> udostępnia interfejsy do generowania kodu źródłowego z grafów obiektów CodeDOM i do zarządzania kompilacją z obsługiwanymi kompilatorami. Dostawca kodu może utworzyć kod źródłowy w określonym języku programowania zgodnie z wykresem CodeDOM. Klasa, która pochodzi od <xref:System.CodeDom.Compiler.CodeDomProvider>, zazwyczaj udostępnia metody generowania i kompilowania kodu dla języka obsługiwanego przez dostawcę.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Generowanie kodu źródłowego przy użyciu dostawcy kodu CodeDOM  
 Aby wygenerować kod źródłowy w określonym języku, potrzebny jest wykres CodeDOM, który reprezentuje strukturę kodu źródłowego do wygenerowania.  
  
 Poniższy przykład pokazuje, jak utworzyć wystąpienie <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Wykres generowania kodu jest zwykle zawarty w <xref:System.CodeDom.CodeCompileUnit>. Aby wygenerować kod dla **CodeCompileUnit** zawierającego wykres CodeDOM, wywołaj metodę <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> dostawcy kodu. Ta metoda ma parametr <xref:System.IO.TextWriter>, którego używa do generowania kodu źródłowego, więc czasami konieczne jest utworzenie elementu **TextWriter** , do którego można pisać. Poniższy przykład demonstruje generowanie kodu z **CodeCompileUnit** i zapisywanie wygenerowanego kodu źródłowego do pliku o nazwie HelloWorld.cs.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Używanie dostawcy kodu CodeDOM do kompilowania zestawów  
 **Wywoływanie kompilacji**  
  
 Aby skompilować zestaw przy użyciu dostawcy CodeDom, musisz mieć kod źródłowy do skompilowania w języku, dla którego masz kompilator, lub wykres CodeDOM, który może zostać wygenerowany przez kod źródłowy do skompilowania.  
  
 Jeśli kompilujesz z wykresu CodeDOM, Przekaż <xref:System.CodeDom.CodeCompileUnit> zawierający wykres do metody <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> dostawcy kodu. Jeśli masz plik kodu źródłowego w języku, który jest rozpoznawany przez kompilator, przekaż nazwę pliku zawierającego kod źródłowy do metody <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> dostawcy CodeDom. Możesz również przekazać ciąg zawierający kod źródłowy w języku, który kompilator rozumie do metody <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> dostawcy CodeDom.  
  
 **Konfigurowanie parametrów kompilacji**  
  
 Wszystkie standardowe metody kompilacji — wywoływanie metod dostawcy CodeDom mają parametr typu <xref:System.CodeDom.Compiler.CompilerParameters>, który wskazuje opcje do użycia dla kompilacji.  
  
 Możesz określić nazwę pliku dla zestawu wyjściowego we właściwości <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> **CompilerParameters**. W przeciwnym razie zostanie użyta domyślna nazwa pliku wyjściowego.  
  
 Domyślnie nowy **CompilerParameters** jest inicjowany z właściwością <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> ustawioną na **wartość false**. W przypadku kompilowania programu wykonywalnego należy ustawić **wartość true**dla właściwości **GenerateExecutable** . Gdy **GenerateExecutable** ma wartość **false**, kompilator wygeneruje bibliotekę klas.  
  
 Jeśli kompilujesz plik wykonywalny z wykresu CodeDOM, <xref:System.CodeDom.CodeEntryPointMethod> musi być zdefiniowany w grafie. Jeśli istnieje wiele punktów wejścia kodu, może być konieczne ustawienie właściwości <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> **CompilerParameters** na nazwę klasy, która definiuje punkt wejścia do użycia.  
  
 Aby dołączyć informacje debugowania w wygenerowanym pliku wykonywalnym, ustaw właściwość <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> na **true**.  
  
 Jeśli projekt odwołuje się do dowolnych zestawów, należy określić nazwy zestawów jako elementy w <xref:System.Collections.Specialized.StringCollection> jako właściwość <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> **CompilerParameters** używanego podczas wywoływania kompilacji.  
  
 Można skompilować zestaw, który jest zapisywana w pamięci, a nie na dysku, ustawiając właściwość <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> na **true**. Gdy zestaw jest generowany w pamięci, kod może uzyskać odwołanie do wygenerowanego zestawu z właściwości <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> <xref:System.CodeDom.Compiler.CompilerResults>. Jeśli zestaw jest zapisywana na dysku, można uzyskać ścieżkę do wygenerowanego zestawu z właściwości <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> **CompilerResults**.  
  
 Aby określić niestandardowy ciąg argumentów wiersza polecenia, który ma być używany podczas wywoływania procesu kompilacji, należy ustawić ciąg we właściwości <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>.  
  
 Jeśli token zabezpieczający Win32 jest wymagany do wywołania procesu kompilatora, należy określić token we właściwości <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A>.  
  
 Aby połączyć plik zasobów Win32 do skompilowanego zestawu, należy określić nazwę pliku zasobów Win32 we właściwości <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A>.  
  
 Aby określić poziom ostrzeżeń, dla którego ma zostać zatrzymana kompilacja, ustaw właściwość <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> na liczbę całkowitą reprezentującą poziom ostrzeżeń, dla którego ma zostać zatrzymana kompilacja. Możesz również skonfigurować kompilator, aby zatrzymać kompilację, jeśli są wyświetlane ostrzeżenia, ustawiając właściwość <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> na **true**.  
  
 Poniższy przykład kodu demonstruje Kompilowanie pliku źródłowego przy użyciu dostawcy CodeDom pochodnego od klasy <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Języki z zapoczątkową pomocą techniczną  
 .NET Framework zapewnia kompilatory kodu i generatory kodu dla następujących języków: C#, Visual Basic, C++i JScript. Obsługę CodeDOM można rozszerzyć do innych języków przez implementację generatorów kodu specyficznych dla języka i kompilatorów kodu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [Dynamiczne generowanie i kompilacja kodu źródłowego](dynamic-source-code-generation-and-compilation.md)
- [Zwięzłe odwołanie CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))
