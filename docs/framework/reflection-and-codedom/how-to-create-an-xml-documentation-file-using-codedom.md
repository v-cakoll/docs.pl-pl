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
ms.openlocfilehash: 8086a512d117767127260bcf779fc11555cd67dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632832"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="ce7fc-102">Instrukcje: Tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ce7fc-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="ce7fc-103">CodeDOM może służyć do tworzenia kodu, który generuje dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="ce7fc-104">Proces obejmuje tworzenie wykresu CodeDOM, który zawiera komentarze dokumentacji XML: generowanie kodu i kompilowania wygenerowanego kodu przy użyciu opcji kompilatora, który tworzy dane wyjściowe XML dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="ce7fc-105">Aby utworzyć wykres CodeDOM, który zawiera komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="ce7fc-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1.  <span data-ttu-id="ce7fc-106">Utwórz <xref:System.CodeDom.CodeCompileUnit> zawierający wykres CodeDOM dla przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2.  <span data-ttu-id="ce7fc-107">Użyj <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktora z `docComment` parametr `true` do tworzenia elementów komentarzy dokumentacji XML i tekst.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="ce7fc-108">Aby wygenerować kod z elementu CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="ce7fc-108">To generate the code from the CodeCompileUnit</span></span>  
  
1.  <span data-ttu-id="ce7fc-109">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodę, aby wygenerować kod i utworzyć plik źródłowy do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="ce7fc-110">Aby skompilować kod i wygenerować plik dokumentacji</span><span class="sxs-lookup"><span data-stu-id="ce7fc-110">To compile the code and generate the documentation file</span></span>  
  
1.  <span data-ttu-id="ce7fc-111">Dodaj **/doc** opcji kompilatora <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> właściwość <xref:System.CodeDom.Compiler.CompilerParameters> i przekazać obiekt do <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodę w celu utworzenia pliku dokumentacji XML, gdy kod jest kompilowany.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="ce7fc-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce7fc-112">Example</span></span>  
 <span data-ttu-id="ce7fc-113">Poniższy przykład kodu tworzy wykres CodeDOM z komentarzami dokumentacji, generuje plik kodu z wykresu i kompiluje plik oraz skojarzonego pliku dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="ce7fc-114">Przykład kodu tworzy w następującej dokumentacji XML w pliku HelloWorldDoc.xml.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce7fc-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ce7fc-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ce7fc-116">Poniższy przykład kodu wymaga `FullTrust` zestawu uprawnień Wykonywanie pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ce7fc-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7fc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce7fc-117">See also</span></span>
- [<span data-ttu-id="ce7fc-118">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="ce7fc-118">Documenting Your Code with XML</span></span>](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="ce7fc-119">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="ce7fc-119">XML Documentation Comments</span></span>](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [<span data-ttu-id="ce7fc-120">Dokumentacja XML</span><span class="sxs-lookup"><span data-stu-id="ce7fc-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
