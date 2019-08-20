---
title: -doc (C# opcje kompilatora)
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
ms.openlocfilehash: e3abb868ff9c9418c7cc565ae667b8225ac9e6e4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603039"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="df97a-102">-doc (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="df97a-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="df97a-103">Opcja **-doc** umożliwia umieszczenie komentarzy do dokumentacji w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="df97a-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df97a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df97a-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="df97a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="df97a-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="df97a-106">Plik wyjściowy dla XML, który jest wypełniony komentarzami w plikach kodu źródłowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="df97a-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df97a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df97a-107">Remarks</span></span>  
 <span data-ttu-id="df97a-108">W plikach kodu źródłowego Komentarze do dokumentacji, które poprzedzają następujące elementy, mogą być przetwarzane i dodawane do pliku XML:</span><span class="sxs-lookup"><span data-stu-id="df97a-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="df97a-109">Takie typy zdefiniowane przez użytkownika jako [Klasa](../keywords/class.md), [Delegat](../keywords/delegate.md)lub [interfejs](../keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="df97a-109">Such user-defined types as a [class](../keywords/class.md), [delegate](../keywords/delegate.md), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="df97a-110">Takie elementy członkowskie jak pole, [zdarzenie](../keywords/event.md), [Właściwość](../../programming-guide/classes-and-structs/using-properties.md)lub metoda</span><span class="sxs-lookup"><span data-stu-id="df97a-110">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="df97a-111">Plik kodu źródłowego, który zawiera główny, jest wyprowadzany jako pierwszy w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="df97a-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="df97a-112">Aby użyć wygenerowanego pliku XML do użycia z funkcją [IntelliSense](/visualstudio/ide/using-intellisense) , pozwól, aby nazwa pliku XML była taka sama jak zestaw, który ma być obsługiwany, a następnie upewnij się, że plik. XML znajduje się w tym samym katalogu, co zestaw.</span><span class="sxs-lookup"><span data-stu-id="df97a-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="df97a-113">Z tego względu, gdy zestaw jest przywoływany w projekcie programu Visual Studio, można również znaleźć plik. XML.</span><span class="sxs-lookup"><span data-stu-id="df97a-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="df97a-114">Zobacz [dostarczanie komentarzy do kodu](/visualstudio/ide/supplying-xml-code-comments) i aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="df97a-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="df97a-115">O ile nie kompilujesz [elementu with-target: module](./target-module-compiler-option.md), `file` program\<będzie zawierał \<zestaw >/Assembly > Tagi określające nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="df97a-115">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df97a-116">Opcja-doc dotyczy wszystkich plików wejściowych; lub, jeśli jest ustawiony w ustawieniach projektu, wszystkie pliki w projekcie.</span><span class="sxs-lookup"><span data-stu-id="df97a-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="df97a-117">Aby wyłączyć ostrzeżenia związane z komentarzami do dokumentacji dla określonego pliku lub sekcji kodu, użyj [#pragma ostrzeżenie](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="df97a-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="df97a-118">Zapoznaj się z [polecanymi tagami komentarzy do dokumentacji](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) , aby poznać sposoby generowania dokumentacji z komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="df97a-118">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="df97a-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df97a-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="df97a-120">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="df97a-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="df97a-121">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="df97a-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="df97a-122">Zmodyfikuj właściwość **pliku dokumentacji XML** .</span><span class="sxs-lookup"><span data-stu-id="df97a-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="df97a-123">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="df97a-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df97a-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df97a-124">See also</span></span>

- [<span data-ttu-id="df97a-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="df97a-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="df97a-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="df97a-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
