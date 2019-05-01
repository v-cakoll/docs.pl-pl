---
title: 'Instrukcje: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM'
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
ms.openlocfilehash: d4088fe35d919cd579ed9f9a6275db8bb88300fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793279"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Instrukcje: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM
CodeDOM może służyć do tworzenia kodu, który generuje dokumentacji XML. Proces obejmuje tworzenie wykresu CodeDOM, który zawiera komentarze dokumentacji XML: generowanie kodu i kompilowania wygenerowanego kodu przy użyciu opcji kompilatora, który tworzy dane wyjściowe XML dokumentacji.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Aby utworzyć wykres CodeDOM, który zawiera komentarze dokumentacji XML  
  
1. Utwórz <xref:System.CodeDom.CodeCompileUnit> zawierający wykres CodeDOM dla przykładowej aplikacji.  
  
2. Użyj <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktora z `docComment` parametr `true` do tworzenia elementów komentarzy dokumentacji XML i tekst.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Aby wygenerować kod z elementu CodeCompileUnit  
  
1. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę, aby wygenerować kod i utworzyć plik źródłowy do skompilowania.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Aby skompilować kod i wygenerować plik dokumentacji  
  
1. Dodaj **/doc** opcji kompilatora <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwość <xref:System.CodeDom.Compiler.CompilerParameters> i przekazać obiekt do <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodę w celu utworzenia pliku dokumentacji XML, gdy kod jest kompilowany.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy wykres CodeDOM z komentarzami dokumentacji, generuje plik kodu z wykresu i kompiluje plik oraz skojarzonego pliku dokumentacji XML.  
  
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
  
- Poniższy przykład kodu wymaga `FullTrust` zestawu uprawnień Wykonywanie pomyślnie.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentowanie kodu za pomocą XML](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Komentarze dokumentacji XML](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [Dokumentacja XML](/cpp/ide/xml-documentation-visual-cpp)
