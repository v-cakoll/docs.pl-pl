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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81d09188ade29b0cac8985da218494f5373980cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397156"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Poradnik: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM
CodeDOM może służyć do tworzenia kodu, który generuje plik dokumentacji XML. Proces obejmuje tworzenie wykresu CodeDOM, który zawiera komentarze dokumentacji XML: generowanie kodu i kompilowania wygenerowanego kodu z opcją kompilatora, która tworzy dane wyjściowe dokumentacji XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Aby utworzyć wykresu CodeDOM zawierający komentarze dokumentacji XML  
  
1.  Utwórz <xref:System.CodeDom.CodeCompileUnit> zawierający wykresu CodeDOM dla przykładowej aplikacji.  
  
2.  Użyj <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktora z `docComment` parametru `true` do tworzenia elementów komentarzy dokumentacji XML i tekst.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Aby wygenerować kod z elementu CodeCompileUnit  
  
1.  Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody w celu generowania kodu i tworzenia pliku źródłowego ma być kompilowana.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Aby skompilować kod i Generuj plik dokumentacji  
  
1.  Dodaj **/doc** — opcja kompilatora do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwość <xref:System.CodeDom.Compiler.CompilerParameters> obiektu i przekazać obiekt do <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodę w celu utworzenia pliku dokumentacji XML podczas kompilowania kodu.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy wykresu CodeDOM z komentarzy do dokumentacji, generuje plik kodu z wykresu i kompiluje plik oraz skojarzony plik dokumentacji XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Przykład kodu tworzy w następującej dokumentacji XML w pliku HelloWorldDoc.xml.  
  
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
  
-   W tym przykładzie kodu wymaga `FullTrust` zestawu uprawnień do wykonania pomyślnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentowanie kodu za pomocą XML](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Komentarze dokumentacji XML](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [Dokumentacja XML](/cpp/ide/xml-documentation-visual-cpp)
