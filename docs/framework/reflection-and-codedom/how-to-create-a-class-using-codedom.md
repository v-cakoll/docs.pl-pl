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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf244e796dad0f3817a3c5acd1fcda8eaf189e2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395391"
---
# <a name="how-to-create-a-class-using-codedom"></a>Porady: tworzenie klasy za pomocą modelu CodeDOM
Poniższe procedury przedstawiają sposób tworzenia i kompilowania wykresu CodeDOM generujący klasa zawierająca dwa pola, właściwości trzy metody, konstruktora i punktu wejścia.  
  
1.  Tworzenie aplikacji konsoli, który będzie używany kod CodeDOM do generowania kodu źródłowego dla klasy.  
  
     W tym przykładzie generowania klasy o nazwie `Sample`, i wygenerowany kod jest klasa o nazwie `CodeDOMCreatedClass` w pliku o nazwie SampleCode.  
  
2.  Podczas generowania klasy, inicjowanie wykresu CodeDOM i za pomocą modelu CodeDOM metod można zdefiniować elementów członkowskich, Konstruktor i punkt wejścia (`Main` metody) wygenerowanej klasy.  
  
     W tym przykładzie wygenerowana klasa ma dwa pola, trzech właściwości, konstruktora, metody, a `Main` metody.  
  
3.  Podczas generowania klasy, należy utworzyć dostawcy specyficzny dla języka kodu i wywołanie jego <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody do generowania kodu z wykresu.  
  
4.  Skompiluj i uruchom aplikację do generowania kodu.  
  
     W tym przykładzie wygenerowany kod znajduje się w pliku o nazwie SampleCode. Skompiluj i wykonanie tego kodu, aby zobaczyć przykładowe dane wyjściowe.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>Aby utworzyć aplikację, która będzie wykonywał kodu CodeDOM  
  
-   Utwórz klasę aplikacji konsoli, zawiera kod CodeDOM. Definiowanie globalnego pola, które mają być używane w klasie można odwoływać się do zestawu (<xref:System.CodeDom.CodeCompileUnit>) i klasy (<xref:System.CodeDom.CodeTypeDeclaration>), określ nazwę wygenerowanym pliku źródłowym i zadeklarować `Main` metody.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>Aby zainicjować wykresu CodeDOM  
  
-   W konstruktorze klasy aplikacji konsoli zainicjować zestaw i klasa i Dodaj deklaracje odpowiednie do wykresu CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>Aby dodać członków do wykresu CodeDOM  
  
-   Dodaj pola do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberField> obiekty do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   Dodawanie właściwości do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberProperty> obiekty do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   Dodawanie metody do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeMemberMethod> do obiektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   Dodaj Konstruktor do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeConstructor> do obiektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   Dodaj punkt wejścia do wykresu CodeDOM przez dodanie <xref:System.CodeDom.CodeEntryPointMethod> do obiektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwość klasy.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>Aby wygenerować kod z wykresu CodeDOM  
  
-   Generowanie kodu źródłowego z wykresu CodeDOM przez wywołanie metody <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Aby utworzyć wykres i generowania kodu  
  
1.  Dodaj utworzone w poprzednich krokach do metody `Main` metody zdefiniowanej w pierwszym kroku.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  Należy skompilować i uruchomić generowania klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje kod z powyższych kroków.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Po powyższym przykładzie są kompilowane i wykonywane, generuje następujący kod źródłowy.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Kod źródłowy wygenerowanego tworzy następujące dane wyjściowe w przypadku kompilowania i wykonywane.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W tym przykładzie kodu wymaga `FullTrust` zestawu uprawnień do wykonania pomyślnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 [Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
