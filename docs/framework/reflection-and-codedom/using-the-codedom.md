---
title: "Używanie modelu CodeDOM"
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
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cd2b8e8ecb0e5d451ebf3c6823144e4a90e0d79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="using-the-codedom"></a>Używanie modelu CodeDOM
Modelu CodeDOM zawiera typy, które reprezentują wiele typów wspólnych elementów kodu źródłowego. Można zaprojektować program, który tworzy modelu kodu źródłowego za pomocą modelu CodeDOM elementów do łączenia z wykresu obiektu. Ten wykres obiektu może być renderowany jako kodu źródłowego za pomocą modelu CodeDOM generator kodu dla obsługiwanych języków programowania. Modelu CodeDOM mogą służyć do kompilowania kodu źródłowego w ramach zestawu binarnego.  
  
 Niektóre typowe zastosowania modelu CodeDOM obejmują:  
  
-   Generowanie kodu opartego na szablonie: generowanie kodu dla platformy ASP.NET, serwery proxy klienta usług XML sieci Web, kreatorów kodu, projektantów lub innych mechanizmów emitowanie kodu.  
  
-   Dynamiczne kompilowanie: Obsługa kompilacji kodu w jednym lub wielu języków.  
  
## <a name="building-a-codedom-graph"></a>Tworzenie wykresu CodeDOM  
 <xref:System.CodeDom> Przestrzeń nazw zawiera klasy reprezentujący struktury logicznej kodu źródłowego, niezależnie od składni języka.  
  
### <a name="the-structure-of-a-codedom-graph"></a>Struktura wykresu CodeDOM  
 Struktura wykresu CodeDOM przypomina drzewa kontenerów. Najwyższy, lub główny, kontener każdego można skompilować dla wykresu CodeDOM jest <xref:System.CodeDom.CodeCompileUnit>. Każdy element modelu kodu źródłowego musi być połączony do wykresu za pomocą właściwości <xref:System.CodeDom.CodeObject> na wykresie.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Tworzenie modelu kodu źródłowego przykładowy Program Hello World  
 Poniższe wskazówki zawiera przykład sposobu tworzenia wykresu CodeDOM obiekt reprezentujący kod prostej aplikacji Hello World. Aby kod źródłowy pełną w tym przykładzie kodu, zobacz <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tematu.  
  
#### <a name="creating-a-compile-unit"></a>Tworzenie jednostki kompilacji  
 Modelu CodeDOM definiuje obiekt o nazwie <xref:System.CodeDom.CodeCompileUnit>, które odwołują się CodeDOM wykres obiektu, który modele kodu źródłowego, aby skompilować. A **elementu CodeCompileUnit** ma właściwości do przechowywania odwołań do atrybutów, obszary nazw i zestawów.  
  
 Dostawcy CodeDom, które pochodzą z <xref:System.CodeDom.Compiler.CodeDomProvider> klasa zawiera metody, które przetwarzają wykres obiektu odwołuje się **elementu CodeCompileUnit**.  
  
 Aby utworzyć wykres obiektu dla prostej aplikacji, należy utworzyć model kodu źródłowego i odwołania z **elementu CodeCompileUnit**.  
  
 Można utworzyć nową jednostkę kompilacji przy użyciu składni zostało to pokazane w tym przykładzie:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 A <xref:System.CodeDom.CodeSnippetCompileUnit> może zawierać części kodu źródłowego, który jest już w języku docelowym, ale nie można renderować na inny język.  
  
#### <a name="defining-a-namespace"></a>Definiowanie przestrzeni nazw  
 Aby zdefiniować przestrzeni nazw, należy utworzyć <xref:System.CodeDom.CodeNamespace> i przypisać mu nazwę dla niego przy użyciu odpowiedniego konstruktora lub przez ustawienie jej **nazwa** właściwości.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Importowanie przestrzeni nazw  
 Aby dodać dyrektywy importu przestrzeni nazw do przestrzeni nazw, należy dodać <xref:System.CodeDom.CodeNamespaceImport> wskazujące przestrzeni nazw, aby zaimportować **CodeNamespace.Imports** kolekcji.  
  
 Poniższy kod dodaje importu dla **systemu** przestrzeni nazw do **importów** Kolekcja **Element CodeNamespace** o nazwie `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Łączenie elementów kodu do obiektu wykresu  
 Wszystkie elementy kodu, które tworzą wykresu CodeDOM musi być połączone z <xref:System.CodeDom.CodeCompileUnit> będący elementem głównym drzewa przez szereg odwołania między elementami odwoływać się bezpośrednio z właściwości obiektu głównego wykresu. Ustaw obiektu z właściwością obiektu kontenera, aby ustanowić odwołanie z obiektu kontenera.  
  
 Następująca instrukcja dodaje `samples` **Element CodeNamespace** do **przestrzeni nazw** właściwości kolekcji głównego **elementu CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Definiowanie typu  
 Aby zadeklarować klasy, struktury, interfejsu lub wyliczenia za pomocą modelu CodeDOM, Utwórz nową <xref:System.CodeDom.CodeTypeDeclaration>i przypisz mu nazwę. W poniższym przykładzie pokazano, to można ustawić przy użyciu przeładowania konstruktora **nazwa** właściwości:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Aby dodać typ do przestrzeni nazw, należy dodać <xref:System.CodeDom.CodeTypeDeclaration> reprezentujący typu do dodania do przestrzeni nazw do **typy** Kolekcja **Element CodeNamespace**.  
  
 W poniższym przykładzie pokazano, jak dodać klasę o nazwie `class1` do **Element CodeNamespace** o nazwie `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Dodawanie elementów członkowskich klasy do klasy  
 <xref:System.CodeDom> Przestrzeń nazw zawiera różne elementy, które mogą służyć do reprezentowania elementów członkowskich klasy. Każdy element członkowski klasy mogą być dodawane do **członków** kolekcji <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Definiowanie metoda punktu wejścia w kodzie pliku wykonywalnego  
 Jeśli tworzysz kod program wykonywalny, należy wskazać punkt wejścia programu, tworząc <xref:System.CodeDom.CodeEntryPointMethod> do metody w programu, które należy rozpocząć wykonywania reprezentowania.  
  
 W poniższym przykładzie pokazano sposób definiowania metoda punktu wejścia, który zawiera <xref:System.CodeDom.CodeMethodInvokeExpression> wywołującym **System.Console.WriteLine** do drukowania "Witaj świecie!":  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Następująca instrukcja dodaje metodę punktu wejścia o nazwie `Start` do **członków** Kolekcja `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Teraz <xref:System.CodeDom.CodeCompileUnit> o nazwie `compileUnit` zawiera wykresu CodeDOM dla prosty program Hello World. Aby uzyskać informacje na generowanie i kompilowanie kodu z wykresu CodeDOM, zobacz [generowanie kodu źródłowego i kompilowanie programu z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>Więcej informacji na temat tworzenia wykresu CodeDOM  
 Modelu CodeDOM obsługuje wiele typów wspólnych elementów kodu w językach programowania, które obsługują środowisko uruchomieniowe języka wspólnego. Modelu CodeDOM nie został zaprojektowany do przekazywania elementów do reprezentowania wszystkich możliwości funkcji języka programowania. Kod, który nie może być reprezentowana łatwo CodeDOM elementów można hermetyzowane w <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, lub <xref:System.CodeDom.CodeSnippetCompileUnit>. Jednak fragmentów nie można przetłumaczyć na inne języki automatycznie za pomocą modelu CodeDOM.  
  
 Dokumentacja dla każdego z typów CodeDOM, zobacz dokumentację odwołanie <xref:System.CodeDom> przestrzeni nazw.  
  
 Szybkie wykresu można znaleźć elementu CodeDOM, który reprezentuje element kodu dla określonego typu, zobacz [CodeDOM krótkimi opisami](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).
