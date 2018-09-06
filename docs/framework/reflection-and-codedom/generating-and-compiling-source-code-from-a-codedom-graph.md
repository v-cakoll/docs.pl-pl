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
ms.openlocfilehash: f5d1546bb9c47d30806d857fa55e1d19fdc2c777
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800579"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM
<xref:System.CodeDom.Compiler> Przestrzeń nazw zawiera interfejsy do generowania kodu źródłowego z wykresu obiektu CodeDOM i zarządzania kompilacji za pomocą obsługiwane kompilatory. Dostawcy kodu może wygenerować kod źródłowy w języku programowania określonym zgodnie z wykresu CodeDOM. Klasa, która pochodzi od klasy <xref:System.CodeDom.Compiler.CodeDomProvider> zazwyczaj może zapewnić metody dla Generowanie i kompilowanie kodu dla języka dostawca obsługuje.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Za pomocą dostawcy kodu CodeDOM, aby wygenerować kod źródłowy  
 Aby wygenerować kod źródłowy w określonym języku, należy wykresu CodeDOM, który reprezentuje strukturę kodu źródłowego do wygenerowania.  
  
 Poniższy przykład pokazuje, jak utworzyć wystąpienie <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Wykres dla generowania kodu jest zwykle są zawarte w <xref:System.CodeDom.CodeCompileUnit>. Aby wygenerować kod dla **elementu CodeCompileUnit** zawierającą wykresu CodeDOM, wywołaj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody dostawcy kodu. Ta metoda ma parametr <xref:System.IO.TextWriter> używaną do generowania kodu źródłowego, więc czasami trzeba najpierw utworzyć **TextWriter** , mogą być zapisywane. W poniższym przykładzie pokazano generowanie kodu z **elementu CodeCompileUnit** i pisanie kodu wygenerowanego źródła w pliku o nazwie HelloWorld.cs.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Kompilowanie zestawów przy użyciu dostawcy kodu CodeDOM  
 **Wywoływanie kompilacji**  
  
 Aby skompilować zestawu przy użyciu dostawcy CodeDom, musi być albo kod źródłowy do skompilowania w języku, do której masz kompilatora lub modelu CodeDOM wykresu tego źródła kodu, aby skompilować mogą być generowane z.  
  
 Jeśli kompilujesz z wykresu CodeDOM, przekazać <xref:System.CodeDom.CodeCompileUnit> zawierający wykres, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metody dostawcy kodu. Jeśli masz plik kodu źródłowego w języku, który kompilator rozpoznaje, przekazać nazwę pliku zawierającego kod źródłowy w celu <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metody dostawcy CodeDom. Można również przekazać ciąg zawierający kod źródłowy w języku, który rozumie kompilator, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metody dostawcy CodeDom.  
  
 **Konfigurowanie parametrów kompilacji**  
  
 Wszystkie standardowe metody wywoływania kompilacji dostawcy CodeDom ma parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> oznacza to, opcje, które będą używane dla kompilacji.  
  
 Można określić nazwę pliku dla zestawu wyjściowego w <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> właściwość **CompilerParameters**. W przeciwnym razie posłuży domyślną nazwę pliku wyjściowego.  
  
 Domyślnie nowy **CompilerParameters** jest inicjowany za pomocą jego <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> właściwością **false**. Jeśli kompilujesz program wykonywalny, musisz ustawić **GenerateExecutable** właściwości **true**. Gdy **GenerateExecutable** ustawiono **false**, kompilator wygeneruje bibliotekę klas.  
  
 Jeśli kompilacja pliku wykonywalnego z wykresu CodeDOM <xref:System.CodeDom.CodeEntryPointMethod> muszą być zdefiniowane na wykresie. Jeśli istnieje wiele punktów wejścia kodu, może być konieczne Ustawianie <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> właściwość **CompilerParameters** na nazwę klasy, która definiuje punkt wejścia do użycia.  
  
 Aby dołączyć informacje o debugowaniu wygenerowany plik wykonywalny, należy ustawić <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> właściwości **true**.  
  
 Jeśli projekt odwołuje się do wszystkich zestawów, należy określić nazwy zestawu jako elementy <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> właściwość **CompilerParameters** użycia podczas wywoływania kompilacji.  
  
 Można też kompilować zestaw, który jest zapisywany w pamięci, a nie na dysku, ustawiając <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> właściwości **true**. Podczas generowania zestawu w pamięci, Twój kod może uzyskać odwołanie do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> właściwość <xref:System.CodeDom.Compiler.CompilerResults>. Jeśli zestaw został napisany na dysku, można uzyskać ścieżki do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> właściwość **CompilerResults**.  
  
 Aby określić ciąg niestandardowe argumenty wiersza polecenia do użycia podczas wywoływania procesu kompilacji, należy określić ciąg <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości.  
  
 W przypadku systemu Win32 token zabezpieczający jest wymagany do wywołania proces kompilatora, należy określić token w <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> właściwości.  
  
 Aby połączyć pliku zasobów Win32 w skompilowanym zestawie, określ nazwę pliku zasobów Win32 w <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> właściwości.  
  
 Aby określić poziom ostrzeżeń, od którego należy zatrzymać kompilacji, ustaw <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> właściwości na liczbę całkowitą reprezentującą poziom ostrzeżeń, od którego należy zatrzymać kompilację. Można również skonfigurować kompilator, aby zatrzymać kompilacji, jeśli nie zostaną napotkane ostrzeżenia, ustawiając <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> właściwości **true**.  
  
 Poniższy przykład kodu demonstruje, kompilowanie pliku źródłowego, za pomocą dostawcy CodeDom pochodną <xref:System.CodeDom.Compiler.CodeDomProvider> klasy.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Języków z początkową obsługą  
 Program .NET Framework oferuje kompilatory kodu i generatorów kodu dla następujących języków: językach C#, Visual Basic, C++ i JScript. Obsługa codeDOM można rozszerzyć do innych języków, implementowanie generatorów kodu specyficznego dla języka i kompilatory kodu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [Dynamiczne generowanie i kompilacja kodu źródłowego](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [CodeDOM — podręczny wykaz](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
