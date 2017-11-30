---
title: -doc (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae3d6e1ffdaaa3245a51005070b16041c16dadae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="doc-c-compiler-options"></a><span data-ttu-id="65eb6-102">/doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="65eb6-102">/doc (C# Compiler Options)</span></span>
<span data-ttu-id="65eb6-103">**/Doc** opcja pozwala na umieszczenie komentarzy do dokumentacji w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="65eb6-103">The **/doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65eb6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65eb6-104">Syntax</span></span>  
  
```console  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="65eb6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="65eb6-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="65eb6-106">Plik wyjściowy XML, który jest wypełniana komentarze w plikach źródłowych kodu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="65eb6-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65eb6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65eb6-107">Remarks</span></span>  
 <span data-ttu-id="65eb6-108">W pliki kodu źródłowego komentarzy do dokumentacji poprzedzających poniżej można przetworzyć i dodane do pliku XML:</span><span class="sxs-lookup"><span data-stu-id="65eb6-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
-   <span data-ttu-id="65eb6-109">Takie typy danych zdefiniowane przez użytkownika jako [klasy](../../../csharp/language-reference/keywords/class.md), [delegować](../../../csharp/language-reference/keywords/delegate.md), lub [— interfejs](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="65eb6-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
-   <span data-ttu-id="65eb6-110">Takie elementy członkowskie jako pole, [zdarzeń](../../../csharp/language-reference/keywords/event.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md), lub — metoda</span><span class="sxs-lookup"><span data-stu-id="65eb6-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="65eb6-111">Pliku kodu źródłowego, który zawiera główny najpierw są kierowane do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="65eb6-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="65eb6-112">Aby użyć pliku .xml wygenerowany do użycia z [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, pozostawić nazwę pliku w pliku XML, być takie same jak zestawu ma być obsługuje, a następnie sprawdź, czy plik XML znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="65eb6-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="65eb6-113">W związku z tym gdy zestaw odwołuje się projekt programu Visual Studio, plik XML znajduje się także.</span><span class="sxs-lookup"><span data-stu-id="65eb6-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="65eb6-114">Zobacz [dostarczanie komentarze w kodzie](/visualstudio/ide/supplying-xml-code-comments) i uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="65eb6-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="65eb6-115">O ile kompilacji z [/target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` będzie zawierać \<zestawu > \< /Assembly > tagi, określając nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="65eb6-115">Unless you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65eb6-116">Opcja/doc ma zastosowanie do wszystkich plików wejściowych; lub, w przypadku ustawienia w ustawieniach projektu, wszystkie pliki w projekcie.</span><span class="sxs-lookup"><span data-stu-id="65eb6-116">The /doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="65eb6-117">Aby wyłączyć ostrzeżenia dotyczące komentarzy do dokumentacji dla określonego pliku lub części kodu, należy użyć [ostrzeżenie #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="65eb6-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="65eb6-118">Zobacz [tagi zalecane dla komentarzy do dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) dotyczące metod do generowania dokumentacji komentarze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="65eb6-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="65eb6-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="65eb6-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="65eb6-120">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="65eb6-120">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="65eb6-121">Kliknij przycisk **kompilacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="65eb6-121">Click the **Build** tab.</span></span>  
  
3.  <span data-ttu-id="65eb6-122">Modyfikowanie **pliku dokumentacji XML** właściwości.</span><span class="sxs-lookup"><span data-stu-id="65eb6-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="65eb6-123">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="65eb6-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65eb6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65eb6-124">See Also</span></span>  
 [<span data-ttu-id="65eb6-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="65eb6-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="65eb6-126">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="65eb6-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
