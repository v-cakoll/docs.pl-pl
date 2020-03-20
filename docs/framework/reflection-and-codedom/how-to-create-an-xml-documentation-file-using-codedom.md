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
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="e8209-102">Poradnik: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="e8209-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="e8209-103">CodeDOM może służyć do tworzenia kodu, który generuje dokumentację XML.</span><span class="sxs-lookup"><span data-stu-id="e8209-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="e8209-104">Proces polega na utworzeniu wykresu CodeDOM, który zawiera komentarze dokumentacji XML, generowanie kodu i kompilowanie wygenerowanego kodu za pomocą opcji kompilatora, która tworzy dane wyjściowe dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="e8209-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="e8209-105">Aby utworzyć wykres CodeDOM zawierający komentarze do dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="e8209-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1. <span data-ttu-id="e8209-106">Utwórz <xref:System.CodeDom.CodeCompileUnit> zawierający wykres CodeDOM dla przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8209-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="e8209-107">Użyj <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktora `docComment` z `true` parametrem ustawionym, aby utworzyć elementy komentarza dokumentacji XML i tekst.</span><span class="sxs-lookup"><span data-stu-id="e8209-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="e8209-108">Aby wygenerować kod z CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="e8209-108">To generate the code from the CodeCompileUnit</span></span>  
  
1. <span data-ttu-id="e8209-109">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> tej metody, aby wygenerować kod i utworzyć plik źródłowy do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="e8209-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="e8209-110">Aby skompilować kod i wygenerować plik dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e8209-110">To compile the code and generate the documentation file</span></span>  
  
1. <span data-ttu-id="e8209-111">Dodaj opcję **kompilatora /doc** do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwości <xref:System.CodeDom.Compiler.CompilerParameters> obiektu i <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> przekaż obiekt do metody, aby utworzyć plik dokumentacji XML podczas kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="e8209-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="e8209-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8209-112">Example</span></span>  
 <span data-ttu-id="e8209-113">Poniższy przykład kodu tworzy wykres CodeDOM z komentarzami dokumentacji, generuje plik kodu z wykresu i kompiluje plik i tworzy skojarzony plik dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="e8209-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="e8209-114">Przykładowy kod tworzy następującą dokumentację XML w pliku HelloWorldDoc.xml.</span><span class="sxs-lookup"><span data-stu-id="e8209-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8209-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e8209-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="e8209-116">W tym przykładzie kodu wymaga `FullTrust` zestawu uprawnień do pomyślnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="e8209-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8209-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8209-117">See also</span></span>

- [<span data-ttu-id="e8209-118">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="e8209-118">Documenting Your Code with XML</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="e8209-119">Komentarze do dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="e8209-119">XML Documentation Comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="e8209-120">Dokumentacja XML</span><span class="sxs-lookup"><span data-stu-id="e8209-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
