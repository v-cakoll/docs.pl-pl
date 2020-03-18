---
title: -doc (Opcje kompilatora C#)
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
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422970"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="72ace-102">-doc (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="72ace-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="72ace-103">Opcja **-doc** umożliwia umieszczanie komentarzy dokumentacji w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="72ace-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ace-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ace-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="72ace-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="72ace-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="72ace-106">Plik wyjściowy dla języka XML, który jest wypełniany komentarzami w plikach kodu źródłowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="72ace-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72ace-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72ace-107">Remarks</span></span>  
 <span data-ttu-id="72ace-108">W plikach kodu źródłowego komentarze dokumentacji, które poprzedzają następujące czynności, mogą być przetwarzane i dodawane do pliku XML:</span><span class="sxs-lookup"><span data-stu-id="72ace-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="72ace-109">Takie typy zdefiniowane przez użytkownika jako [klasa,](../keywords/class.md) [delegat](../builtin-types/reference-types.md#the-delegate-type)lub [interfejs](../keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="72ace-109">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="72ace-110">Takie elementy członkowskie, jak pole, [zdarzenie,](../keywords/event.md) [właściwość](../../programming-guide/classes-and-structs/using-properties.md)lub metoda</span><span class="sxs-lookup"><span data-stu-id="72ace-110">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="72ace-111">Plik kodu źródłowego, który zawiera Main jest najpierw wyprowadzany do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="72ace-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="72ace-112">Aby użyć wygenerowanego pliku xml do użycia z funkcją [IntelliSense,](/visualstudio/ide/using-intellisense) niech nazwa pliku xml będzie taka sama jak zestaw, który chcesz obsługiwać, a następnie upewnij się, że plik xml znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="72ace-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="72ace-113">W związku z tym gdy zestaw odwołuje się do projektu programu Visual Studio, plik xml znajduje się również.</span><span class="sxs-lookup"><span data-stu-id="72ace-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="72ace-114">Zobacz [dostarczanie komentarzy do kodu](/visualstudio/ide/reference/generate-xml-documentation-comments) i uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="72ace-114">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="72ace-115">Chyba że skompilować z [-target:module](./target-module-compiler-option.md), `file` będzie zawierać \<zestaw>\</zestaw> tagów określających nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="72ace-115">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72ace-116">Opcja -doc ma zastosowanie do wszystkich plików wejściowych; lub, jeśli ustawiono w ustawieniach projektu, wszystkie pliki w projekcie.</span><span class="sxs-lookup"><span data-stu-id="72ace-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="72ace-117">Aby wyłączyć ostrzeżenia związane z komentarzami dokumentacji dla określonego pliku lub sekcji kodu, należy użyć [ostrzeżenia #pragma](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="72ace-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="72ace-118">Zobacz [Zalecane tagi dla dokumentacji Komentarze](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) dla sposobów generowania dokumentacji z komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="72ace-118">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="72ace-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72ace-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="72ace-120">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="72ace-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="72ace-121">Kliknij kartę **Kompilacja.**</span><span class="sxs-lookup"><span data-stu-id="72ace-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="72ace-122">Zmodyfikuj właściwość **pliku dokumentacji XML.**</span><span class="sxs-lookup"><span data-stu-id="72ace-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="72ace-123">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="72ace-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ace-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72ace-124">See also</span></span>

- [<span data-ttu-id="72ace-125">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="72ace-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="72ace-126">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="72ace-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
