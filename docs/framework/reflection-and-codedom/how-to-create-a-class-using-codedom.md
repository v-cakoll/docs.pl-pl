---
title: 'Instrukcje: Tworzenie klasy za pomocą modelu CodeDOM'
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
ms.openlocfilehash: 906007902c6b66d88da0d3145625e56f2a7e2b55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592518"
---
# <a name="how-to-create-a-class-using-codedom"></a>Instrukcje: Tworzenie klasy za pomocą modelu CodeDOM
Poniższe procedury pokazują, jak utworzyć i skompilować wykresu CodeDOM, który generuje klasę zawierający dwa pola, trzy właściwości, metody, Konstruktor i punktu wejścia.  
  
1. Utwórz aplikację konsolową, która będzie używać kodu CodeDOM, aby wygenerować kod źródłowy dla klasy.  
  
     W tym przykładzie Generowanie klasy o nazwie `Sample`, i wygenerowany kod jest klasę o nazwie `CodeDOMCreatedClass` w pliku o nazwie SampleCode.  
  
2. Podczas generowania klasy, zainicjować wykresu CodeDOM i definiowanie elementów członkowskich, Konstruktor i punktu wejścia przy użyciu metod CodeDOM (`Main` metoda) wygenerowanej klasy.  
  
     W tym przykładzie, wygenerowana klasa ma dwa pola, trzy właściwości, Konstruktor, metody i `Main` metody.  
  
3. Podczas generowania klasy, utworzyć dostawcy kodu specyficznego dla języka i wywołanie jego <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę w celu wygenerowania kodu z wykresu.  
  
4. Skompiluj i uruchom aplikację do generowania kodu.  
  
     W tym przykładzie wygenerowany kod znajduje się w pliku o nazwie SampleCode. Skompiluj i wykonać ten kod, aby wyświetlić przykładowe dane wyjściowe.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>Do tworzenia aplikacji, które spowodują wykonanie kodu CodeDOM  
  
- Tworzenie klasy aplikacji konsoli w celu uwzględnienia kodu CodeDOM. Zdefiniuj globalne pola, które mają być używane w klasie, aby odwoływać się do zestawu (<xref:System.CodeDom.CodeCompileUnit>) i klasy (<xref:System.CodeDom.CodeTypeDeclaration>), określ nazwę pliku wygenerowanego źródła i zadeklarować `Main` metody.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>Aby zainicjować wykresu CodeDOM  
  
- W konstruktorze klasy aplikacji konsoli zainicjować zestaw i klasa i Dodaj właściwe deklaracje do wykresu CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>Aby dodać członków do wykresu CodeDOM  
  
- Dodaj pola do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeMemberField> obiekty do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- Dodawanie właściwości do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeMemberProperty> obiekty do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- Dodawanie metody do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeMemberMethod> obiekt <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- Dodaj Konstruktor do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeConstructor> obiekt <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- Dodaj punkt wejścia do wykresu CodeDOM, dodając <xref:System.CodeDom.CodeEntryPointMethod> obiekt <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> właściwości klasy.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>Do generowania kodu z wykresu CodeDOM  
  
- Generowanie kodu źródłowego z wykresu CodeDOM, wywołując <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Aby utworzyć wykres i generowania kodu  
  
1. Dodaj metody, utworzony w poprzednich krokach do `Main` metody zdefiniowanej w pierwszym kroku.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. Skompilować i uruchomić generowania klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu zawiera kod z poprzednich kroków.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Gdy poprzedni przykład jest skompilowany i wykonany, tworzy następujące kodu źródłowego.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Kod źródłowy wygenerowanego generuje następujące dane wyjściowe, gdy skompilowany i wykonany.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Poniższy przykład kodu wymaga `FullTrust` zestawu uprawnień Wykonywanie pomyślnie.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [Generowanie i kompilowanie kodu źródłowego z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
