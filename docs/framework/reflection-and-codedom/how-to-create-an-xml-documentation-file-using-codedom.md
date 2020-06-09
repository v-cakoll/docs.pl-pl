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
ms.openlocfilehash: b9e11a51048733dbfc42ff9f575e18effc80db07
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596249"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Instrukcje: Tworzenie pliku dokumentacji XML przy użyciu CodeDOM

CodeDOM można użyć do utworzenia kodu, który generuje dokumentację XML. Proces obejmuje tworzenie wykresu CodeDOM, który zawiera komentarze dokumentacji XML, generowanie kodu i kompilowanie wygenerowanego kodu z opcją kompilatora, która tworzy dane wyjściowe dokumentacji XML.  
  
## <a name="create-a-codedom-graph"></a>Tworzenie wykresu CodeDOM
  
1. Utwórz <xref:System.CodeDom.CodeCompileUnit> zawierający wykres CodeDOM dla przykładowej aplikacji.  
  
2. Użyj <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktora z `docComment` parametrem ustawionym na, aby `true` utworzyć elementy komentarza dokumentacji XML i tekst.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a>Generowanie kodu z CodeCompileUnit
  
1. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody, aby wygenerować kod i utworzyć plik źródłowy do skompilowania.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a>Kompiluj kod i wygeneruj plik dokumentacji
  
1. Dodaj opcję kompilatora **/doc** do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości <xref:System.CodeDom.Compiler.CompilerParameters> obiektu i przekaż obiekt do <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metody, aby utworzyć plik dokumentacji XML podczas kompilowania kodu.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Przykład

Poniższy przykład kodu tworzy wykres CodeDOM z komentarzami dokumentacji, generuje plik kodu z Grafu i kompiluje plik i tworzy skojarzony plik dokumentacji XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 W przykładzie kodu jest tworzona następująca dokumentacja XML w pliku *HelloWorldDoc. XML* .  
  
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
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
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
  
## <a name="compile-permissions"></a>Kompiluj uprawnienia
  
Ten przykład kodu wymaga `FullTrust` pomyślnego wykonania zestawu uprawnień.
  
## <a name="see-also"></a>Zobacz też

- [Dokumentowanie kodu za pomocą XML (Visual Basic)](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Komentarze dokumentacji XML](../../csharp/programming-guide/xmldoc/index.md)
- [Dokumentacja XML (C++)](/cpp/ide/xml-documentation-visual-cpp)
