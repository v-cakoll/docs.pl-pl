---
title: "Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56e2effec282900101fc0cbe489c76b523184ab2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM
<xref:System.CodeDom.Compiler> Przestrzeń nazw zawiera interfejsy do generowania kodu źródłowego z wykresów CodeDOM obiektu i zarządzania kompilacji z kompilatorów obsługiwane. Dostawca kodu może wygenerować kodu źródłowego w określonym języku programowania zgodnie z wykresu CodeDOM. Klasa, która pochodzi z <xref:System.CodeDom.Compiler.CodeDomProvider> zwykle zapewnia metody dla Generowanie i kompilowanie kodu dla języka dostawca obsługuje.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Generowanie kodu źródłowego za pomocą dostawcy CodeDOM kodu  
 Aby wygenerować kod źródłowy w określonym języku, należy wykresu CodeDOM reprezentujący strukturę aby wygenerować kod źródłowy.  
  
 Poniższy przykład pokazują, jak można utworzyć wystąpienia <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Wykres dla generowania kodu zazwyczaj znajduje się w <xref:System.CodeDom.CodeCompileUnit>. Aby wygenerować kod dla **elementu CodeCompileUnit** zawierający wykresu CodeDOM, należy wywołać <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody dostawcy kodu. Ta metoda ma parametr <xref:System.IO.TextWriter> używaną do generowania kodu źródłowego, dlatego czasami najpierw utworzyć **TextWriter** mogą być zapisywane na. W poniższym przykładzie pokazano generowania kodu z **elementu CodeCompileUnit** i pisanie kodu wygenerowanego źródła w pliku o nazwie HelloWorld.cs.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Za pomocą dostawcy CodeDOM kodu do kompilacji zestawy  
 **Wywoływanie kompilacji**  
  
 Aby skompilować zestawu za pomocą dostawcy CodeDom, musi mieć albo kodu źródłowego, aby skompilować w języku, dla którego masz kompilatora lub CodeDOM wykresów tego źródła może generować kod, aby skompilować.  
  
 Jeśli kompilacja z wykresu CodeDOM przekazać <xref:System.CodeDom.CodeCompileUnit> zawierający wykres tak, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metody dostawcy kodu. Jeśli masz pliku kodu źródłowego w języku, który obsługuje usługę kompilator nazwę pliku zawierającego kod źródłowy, aby przekazać <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metody dostawcy CodeDom. Można również przekazać ciąg zawierający kod źródłowy w języku, który kompilator rozumie, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metody dostawcy CodeDom.  
  
 **Konfigurowanie parametrów kompilacji**  
  
 Wszystkie standardowe metody wywoływania kompilacji dostawcy CodeDom ma parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> wskazujące opcje, które będą używane dla kompilacji.  
  
 Można określić nazwę pliku dla zestawu wyjściowego w <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> właściwość **CompilerParameters**. W przeciwnym razie będzie używana domyślną nazwę pliku wyjściowego.  
  
 Domyślnie nowy **CompilerParameters** jest inicjowany z jego <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> ustawioną właściwość **false**. Jeśli kompilacja program wykonywalny, należy ustawić **GenerateExecutable** właściwości **true**. Gdy **GenerateExecutable** ustawiono **false**, kompilator wygeneruje biblioteki klas.  
  
 Jeśli kompilacja pliku wykonywalnego z wykresu CodeDOM <xref:System.CodeDom.CodeEntryPointMethod> musi być zdefiniowany na wykresie. Jeśli istnieje wiele punktów wejścia kodu, może być konieczne ustawić <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> właściwość **CompilerParameters** na nazwę klasy, która określa punkt wejścia do użycia.  
  
 Aby uwzględnić informacje o debugowaniu w wygenerowanym pliku wykonywalnego, ustaw <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> właściwości **true**.  
  
 Jeśli projekt odwołuje się do żadnych zestawów, należy określić nazwy zestawu jako elementy w <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> właściwość **CompilerParameters** używany podczas wywoływania kompilacji.  
  
 Można utworzyć zestawu, który jest zapisywany w pamięci, a nie na dysku przez ustawienie <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> właściwości **true**. Podczas generowania zestawu w pamięci kodu można uzyskać odwołanie do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> właściwość <xref:System.CodeDom.Compiler.CompilerResults>. Jeśli zestaw jest zapisywany do dysku, można uzyskać ścieżki do wygenerowanego zestawu z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> właściwość **CompilerResults**.  
  
 Aby określić argumenty wiersza polecenia niestandardowych ciąg do użycia podczas wywoływania procesu kompilacji, należy określić ciąg <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości.  
  
 Jeśli token zabezpieczający Win32 jest wymagany do wywołania proces kompilatora, określ token w <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> właściwości.  
  
 Aby połączyć plik zasobów Win32 w skompilowanym zestawie, określ nazwę pliku zasobów Win32 w <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> właściwości.  
  
 Aby określić poziom ostrzeżeń, w którym należy zatrzymać kompilacji, należy ustawić <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> właściwości na liczbę całkowitą reprezentującą poziom ostrzeżenia, na którym zatrzymanie kompilacji. Można również skonfigurować kompilatora zatrzymanie kompilacji, jeśli występują ostrzeżenia przez ustawienie <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> właściwości **true**.  
  
 Poniższy przykład kodu pokazuje kompilowanie pliku źródłowego przy użyciu dostawcy CodeDom pochodną <xref:System.CodeDom.Compiler.CodeDomProvider> klasy.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Języków z początkową obsługą  
 .NET Framework zapewnia kompilatory kodu i generatory kodu dla następujących języków: C#, Visual Basic C++ i JScript. Obsługa codeDOM można rozszerzyć do innych języków zaimplementowanie generatory specyficzny dla języka kodu i kompilatory kodu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [Dynamiczne generowanie i kompilacja kodu źródłowego](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [Krótki przewodnik codeDOM](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
