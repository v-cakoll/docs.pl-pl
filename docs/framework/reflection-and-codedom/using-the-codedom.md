---
title: Używanie modelu CodeDOM
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50ff6e2baaee683674f82cff178eeef7b7e43de4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486215"
---
# <a name="using-the-codedom"></a>Używanie modelu CodeDOM
CodeDOM zawiera typy, które reprezentują wiele typowych elementów kodu źródłowego. Można zaprojektować program, który tworzy model kodu źródłowego za pomocą elementów CodeDOM, aby zamontować wykresu obiektu. Wykres tego obiektu może być renderowany jako kod źródłowy za pomocą generatora kodu CodeDOM dla obsługiwanego języka programowania. CodeDOM może również skompilować kod źródłowy do zestawu binarnego.  
  
 Jedne z typowych zastosowań CodeDom obejmują:  
  
-   Generowanie kodu szablonu: generowanie kodu dla programu ASP.NET, serwerów proxy klienta usług XML sieci Web, kreatorów kodu, projektantów lub innych mechanizmów emitujących kod.  
  
-   Dynamiczna kompilacja: wspieranie kompilacji kodu w jednym lub wielu języków.  
  
## <a name="building-a-codedom-graph"></a>Tworzenie wykresu CodeDOM  
 <xref:System.CodeDom> Przestrzeń nazw zawiera klasy do reprezentowania logicznej struktury kodu źródłowego, niezależnie od składni języka.  
  
### <a name="the-structure-of-a-codedom-graph"></a>Struktura wykresu CodeDOM  
 Struktura wykresu CodeDOM jest drzewo kontenerów. Najważniejsze, lub katalogu głównego, kontener każdego nadawać wykresu CodeDOM <xref:System.CodeDom.CodeCompileUnit>. Każdy element modelu kodu źródłowego musi być połączony z wykresem za pomocą właściwości <xref:System.CodeDom.CodeObject> na wykresie.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Tworzenie modelu kodu źródłowego dla przykładowy Program Hello World  
 Następujące instruktaż zawiera przykład sposobu tworzenia wykresu obiektu CodeDOM, który reprezentuje kod dla prostej aplikacji Hello World. Aby uzyskać pełnego kodu źródłowego dla tego przykładu kodu, zobacz <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tematu.  
  
#### <a name="creating-a-compile-unit"></a>Tworzenie jednostki kompilacji  
 CodeDOM definiuje obiekt o nazwie <xref:System.CodeDom.CodeCompileUnit>, który może odwoływać się do wykresu obiektu CodeDOM, który modeluje kod źródłowy do skompilowania. A **elementu CodeCompileUnit** ma właściwości służąca do przechowywania odwołań do atrybutów, przestrzeni nazw i zestawów.  
  
 Dostawcy CodeDom, które wynikają z <xref:System.CodeDom.Compiler.CodeDomProvider> klasy zawierają metody, które przetwarzają wykres obiektu odwołuje się **elementu CodeCompileUnit**.  
  
 Do utworzenia wykresu obiektu dla prostej aplikacji, należy utworzyć model kodu źródłowego i odwoływać się do niego z **elementu CodeCompileUnit**.  
  
 Możesz utworzyć nową jednostkę kompilacji przy użyciu składni, jak pokazano w tym przykładzie:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 Element <xref:System.CodeDom.CodeSnippetCompileUnit> może zawierać sekcję kodu źródłowego, który jest już w języku docelowym, ale nie może być renderowana na inny język.  
  
#### <a name="defining-a-namespace"></a>Definiowanie przestrzeni nazw  
 Aby zdefiniować obszar nazw, należy utworzyć <xref:System.CodeDom.CodeNamespace> i przypisać mu nazwę, za pomocą odpowiedniego konstruktora lub przez ustawienie jego **nazwa** właściwości.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Importowanie przestrzeni nazw  
 Aby dodać dyrektywę import obszaru nazw do obszaru nazw, należy dodać <xref:System.CodeDom.CodeNamespaceImport> oznacza to, przestrzeń nazw do zaimportowania do **CodeNamespace.Imports** kolekcji.  
  
 Poniższy kod dodaje import dla **systemu** przestrzeń nazw **Importy** zbiór **CodeNamespace** o nazwie `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Łączenie elementów kodu na wykresie obiektu  
 Wszystkie elementy kodu, które tworzą wykres CodeDOM muszą być połączone z <xref:System.CodeDom.CodeCompileUnit> czyli elementem głównym drzewa przez szereg odwołań między elementami wywoływanymi bezpośrednio z właściwości obiektu głównego wykresu. Ustaw obiekt do właściwości obiektu kontenera, aby ustanowić odwołanie z obiektu kontenera.  
  
 Poniższa instrukcja dodaje `samples` **CodeNamespace** do **przestrzenie nazw** kolekcji właściwości głównego **elementu CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Definiowanie typu  
 Aby zadeklarować klasy, struktury, interfejs lub wyliczenie przy użyciu CodeDOM, Utwórz nową <xref:System.CodeDom.CodeTypeDeclaration>i przypisz mu nazwy. Poniższy przykład przedstawia, to za pomocą przeciążenia konstruktora, aby ustawić **nazwa** właściwości:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Aby dodać typ do przestrzeni nazw, należy dodać <xref:System.CodeDom.CodeTypeDeclaration> reprezentujący typu do dodania do obszaru nazw do **typy** zbiór **CodeNamespace**.  
  
 Poniższy przykład pokazuje, jak dodać klasę o nazwie `class1` do **CodeNamespace** o nazwie `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Dodawanie elementów członkowskich klasy do klasy  
 <xref:System.CodeDom> Przestrzeń nazw zapewnia różne elementy, które mogą służyć do reprezentowania członków klasy. Każdy element członkowski klasy mogą być dodawane do **członków** zbiór <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Definiowanie metody punktu wejścia kodu pliku wykonywalnego  
 Jeśli tworzysz kod dla wykonywalnego programu jest wskazanie punktu wejścia programu, tworząc <xref:System.CodeDom.CodeEntryPointMethod> do reprezentowania metody, w której program powinien rozpocząć wykonywanie.  
  
 Poniższy przykład ilustruje sposób definiowania metody punktu wejścia, który zawiera <xref:System.CodeDom.CodeMethodInvokeExpression> wywołująca **System.Console.WriteLine** do drukowania "Hello World!":  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Poniższa instrukcja dodaje metody punktu wejścia o nazwie `Start` do **członków** zbiór `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Teraz <xref:System.CodeDom.CodeCompileUnit> o nazwie `compileUnit` zawiera wykres CodeDOM dla prostego programu Witaj świecie. Aby uzyskać informacje na temat generowania i kompilowania kodu z wykresu CodeDOM, zobacz [generowania kodu źródłowego i kompilacja programu z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>Więcej informacji na temat tworzenia wykresu CodeDOM  
 CodeDOM obsługuje wiele często spotykanych rodzajów elementów kodu w językach programowania, które obsługują środowiska uruchomieniowego języka wspólnego. CodeDOM nie został zaprojektowany w celu zapewnienia elementu do reprezentowania wszystkich możliwych funkcji języka programowania. Kod, który nie może być reprezentowany w prosty sposób z elementami CodeDOM można hermetyzować w <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, lub <xref:System.CodeDom.CodeSnippetCompileUnit>. Jednak fragmentów kodu nie może być przetłumaczone na inne języki automatycznie przez CodeDOM.  
  
 Aby uzyskać dokumentację dla każdego z typów CodeDOM, zobacz dokumentację referencyjną dla <xref:System.CodeDom> przestrzeni nazw.  
  
 Szybkiego wykresu do zlokalizowania elementu CodeDOM, który reprezentuje określony typ elementu kodu, zobacz [CodeDOM — podręczny wykaz](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).
