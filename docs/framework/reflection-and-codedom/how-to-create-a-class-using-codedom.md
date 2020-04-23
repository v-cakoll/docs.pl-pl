---
title: 'Porady: tworzenie klasy za pomocą modelu CodeDOM'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: ff7c9d1593c8e75f9bcaeda6577c7cb941719749
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130195"
---
# <a name="how-to-create-a-class-using-codedom"></a>Porady: tworzenie klasy za pomocą modelu CodeDOM
Poniższe procedury ilustrują sposób tworzenia i kompilowania wykresu CodeDOM, który generuje klasę zawierającą dwa pola, trzy właściwości, metodę, Konstruktor i punkt wejścia.  
  
1. Utwórz aplikację konsolową, która będzie używać kodu CodeDOM do generowania kodu źródłowego dla klasy.  
  
     W tym przykładzie Klasa generująca ma nazwę `Sample`, a wygenerowany kod jest klasą o `CodeDOMCreatedClass` nazwie SampleCode.  
  
2. W klasie generującej zainicjuj wykres CodeDOM i użyj metod CodeDOM, aby zdefiniować elementy członkowskie, Konstruktor i punkt wejścia (`Main` metodę) wygenerowanej klasy.  
  
     W tym przykładzie wygenerowana Klasa ma dwa pola, trzy właściwości, Konstruktor, metodę i `Main` metodę.  
  
3. W klasie generującej Utwórz dostawcę kodu specyficzny dla języka i Wywołaj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę w celu wygenerowania kodu z grafu.  
  
4. Skompiluj i uruchom aplikację w celu wygenerowania kodu.  
  
     W tym przykładzie wygenerowany kod znajduje się w pliku o nazwie SampleCode. Skompiluj i wykonaj ten kod, aby zobaczyć przykładowe dane wyjściowe.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>Aby utworzyć aplikację, która będzie wykonywała kod CodeDOM  
  
- Utwórz klasę aplikacji konsoli, która będzie zawierać kod CodeDOM. Zdefiniuj pola globalne, które mają być używane w klasie, aby odwołać się do zestawu<xref:System.CodeDom.CodeCompileUnit>() i klasy<xref:System.CodeDom.CodeTypeDeclaration>(), określ nazwę wygenerowanego pliku źródłowego i Zadeklaruj `Main` metodę.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>Aby zainicjować wykres CodeDOM  
  
- W konstruktorze klasy aplikacji konsoli, Zainicjuj zestaw i klasę, a następnie Dodaj odpowiednie deklaracje do wykresu CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>Aby dodać elementy członkowskie do wykresu CodeDOM  
  
- Dodaj pola do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberField> obiektów do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- Dodaj właściwości do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberProperty> obiektów do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- Dodaj metodę do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeMemberMethod> obiekt do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- Dodaj Konstruktor do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeConstructor> obiekt do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- Dodaj punkt wejścia do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeEntryPointMethod> obiekt do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>Aby wygenerować kod z wykresu CodeDOM  
  
- Wygeneruj kod źródłowy z grafu CodeDOM, wywołując <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Aby utworzyć Graf i wygenerować kod  
  
1. Dodaj metody utworzone w poprzednich krokach do `Main` metody zdefiniowanej w pierwszym kroku.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. Kompiluj i wykonaj klasę generującą.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje kod z poprzednich kroków.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Gdy poprzedni przykład jest kompilowany i wykonywany, generuje następujący kod źródłowy.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Wygenerowany kod źródłowy generuje następujące dane wyjściowe podczas kompilowania i wykonywania.  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Ten przykład kodu wymaga pomyślnego wykonania zestawu `FullTrust` uprawnień.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie modelu CodeDOM](using-the-codedom.md)
- [Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md)
