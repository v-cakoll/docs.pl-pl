---
title: -doc (opcje kompilatora C#)
ms.date: 07/20/2015
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
ms.openlocfilehash: 24eb3b1a70c420fd0008ea9c202c774592e1d346
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137476"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="878af-102">-doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="878af-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="878af-103">**-Doc** opcja służy do umieszczania komentarzy do dokumentacji w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="878af-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="878af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="878af-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="878af-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="878af-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="878af-106">Plik wyjściowy dla formatu XML, który jest wypełniana przy użyciu komentarzy w plikach kodu źródłowego, kompilacji.</span><span class="sxs-lookup"><span data-stu-id="878af-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="878af-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="878af-107">Remarks</span></span>  
 <span data-ttu-id="878af-108">W plikach kodu źródłowego komentarzy do dokumentacji, które poprzedzają poniżej można przetworzyć i dodawane do pliku XML:</span><span class="sxs-lookup"><span data-stu-id="878af-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
-   <span data-ttu-id="878af-109">Takie typy zdefiniowane przez użytkownika jako [klasy](../../../csharp/language-reference/keywords/class.md), [delegować](../../../csharp/language-reference/keywords/delegate.md), lub [interfejsu](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="878af-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
-   <span data-ttu-id="878af-110">Takich elementów członkowskich jako pole, [zdarzeń](../../../csharp/language-reference/keywords/event.md), [właściwość](../../../csharp/programming-guide/classes-and-structs/using-properties.md), lub metody</span><span class="sxs-lookup"><span data-stu-id="878af-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="878af-111">Pliku kodu źródłowego, który zawiera główny najpierw są kierowane do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="878af-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="878af-112">Aby użyć pliku XML wygenerowanego do użytku z programem [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, umożliwić nazwę pliku w pliku XML, który być taka sama jak zestaw ma być obsługiwane, a następnie sprawdź, czy plik .xml znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="878af-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="878af-113">W związku z tym gdy zestaw jest przywoływana w projekcie programu Visual Studio, pliku XML, który znajduje się także.</span><span class="sxs-lookup"><span data-stu-id="878af-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="878af-114">Zobacz [podawania komentarzy do kodu](/visualstudio/ide/supplying-xml-code-comments) i uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="878af-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="878af-115">Jeśli kompilujesz z [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` będzie zawierać \<zestawu > \< /Assembly > Znaczniki, określając nazwę pliku zawierającego manifest zestawu dla pliku danych wyjściowych Kompilacja.</span><span class="sxs-lookup"><span data-stu-id="878af-115">Unless you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="878af-116">Doc — opcja ma zastosowanie do wszystkich wejściowych plików; lub, jeśli w ustawieniach projektu, wszystkie pliki w projekcie.</span><span class="sxs-lookup"><span data-stu-id="878af-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="878af-117">Aby wyłączyć ostrzeżenia dotyczące komentarzy dokumentacji dla określonego pliku lub sekcji kodu, należy użyć [ostrzeżenie #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="878af-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="878af-118">Zobacz [tagi zalecane dla komentarzy do dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) sposobów generować dokumentację z komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="878af-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="878af-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="878af-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="878af-120">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="878af-120">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="878af-121">Kliknij przycisk **kompilacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="878af-121">Click the **Build** tab.</span></span>  
  
3.  <span data-ttu-id="878af-122">Modyfikowanie **pliku dokumentacji XML** właściwości.</span><span class="sxs-lookup"><span data-stu-id="878af-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="878af-123">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="878af-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878af-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="878af-124">See Also</span></span>  

- [<span data-ttu-id="878af-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="878af-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="878af-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="878af-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
