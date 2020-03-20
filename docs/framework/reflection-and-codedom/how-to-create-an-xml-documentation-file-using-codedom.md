---
title: 'Poradnik: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: a0ccb469a43c3a21a76eaf24fa7ce7b490dd5c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180521"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Poradnik: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM
CodeDOM może służyć do tworzenia kodu, który generuje dokumentację XML. Proces polega na utworzeniu wykresu CodeDOM, który zawiera komentarze dokumentacji XML, generowanie kodu i kompilowanie wygenerowanego kodu za pomocą opcji kompilatora, która tworzy dane wyjściowe dokumentacji XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Aby utworzyć wykres CodeDOM zawierający komentarze do dokumentacji XML  
  
1. Utwórz <xref:System.CodeDom.CodeCompileUnit> zawierający wykres CodeDOM dla przykładowej aplikacji.  
  
2. Użyj <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktora `docComment` z `true` parametrem ustawionym, aby utworzyć elementy komentarza dokumentacji XML i tekst.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Aby wygenerować kod z CodeCompileUnit  
  
1. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> tej metody, aby wygenerować kod i utworzyć plik źródłowy do skompilowania.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Aby skompilować kod i wygenerować plik dokumentacji  
  
1. Dodaj opcję **kompilatora /doc** do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości <xref:System.CodeDom.Compiler.CompilerParameters> obiektu i <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> przekaż obiekt do metody, aby utworzyć plik dokumentacji XML podczas kompilowania kodu.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy wykres CodeDOM z komentarzami dokumentacji, generuje plik kodu z wykresu i kompiluje plik i tworzy skojarzony plik dokumentacji XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Przykładowy kod tworzy następującą dokumentację XML w pliku HelloWorldDoc.xml.  
  
```xml  
<?xml version="1.0" ?>
<doc>  
  <assembly>  
    <name>HelloWorld</name>
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.
        <seealso cref="M:Samples.Class1.Main" />
      </summary>  
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.
        <para>Add a new paragraph to the description.</para>
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- W tym przykładzie kodu wymaga `FullTrust` zestawu uprawnień do pomyślnego wykonania.  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentowanie kodu za pomocą XML](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Komentarze do dokumentacji XML](../../csharp/programming-guide/xmldoc/index.md)
- [Dokumentacja XML](/cpp/ide/xml-documentation-visual-cpp)
