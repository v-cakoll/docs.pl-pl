---
title: -Definiowanie (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 46ceca3a84e8ffbe6d07886c1b93d062f3ccd2d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305263"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="28113-102">-Definiowanie (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="28113-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="28113-103">**— Zdefiniuj** opcja definiuje `name` jako symbol w kodzie źródłowym wszystkie pliki programu.</span><span class="sxs-lookup"><span data-stu-id="28113-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28113-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28113-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="28113-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="28113-105">Arguments</span></span>  
 <span data-ttu-id="28113-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="28113-106">`name`, `name2`</span></span>  
 <span data-ttu-id="28113-107">Nazwa co najmniej jeden symboli, które chcesz zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="28113-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28113-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28113-108">Remarks</span></span>  
 <span data-ttu-id="28113-109">**— Zdefiniuj** opcja ma taki sam skutek jak przy użyciu [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora z tą różnicą, że opcja kompilatora jest aktywna dla wszystkich plików w projekcie.</span><span class="sxs-lookup"><span data-stu-id="28113-109">The **-define** option has the same effect as using a [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="28113-110">Symbol pozostaje zdefiniowany w pliku źródłowym, dopóki [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym usuwa definicję.</span><span class="sxs-lookup"><span data-stu-id="28113-110">A symbol remains defined in a source file until an [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="28113-111">Jeśli używasz define — opcja, `#undef` dyrektywy w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.</span><span class="sxs-lookup"><span data-stu-id="28113-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="28113-112">Można użyć symboli utworzone przez tę opcję z [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), i [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) Aby warunkowo skompilować pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="28113-112">You can use symbols created by this option with [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), and [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="28113-113">**-d** jest krótka forma **— Zdefiniuj**.</span><span class="sxs-lookup"><span data-stu-id="28113-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="28113-114">Można zdefiniować wiele symboli z **— Zdefiniuj** przy użyciu nazwy symbolu średnikami lub przecinkami.</span><span class="sxs-lookup"><span data-stu-id="28113-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="28113-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="28113-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="28113-116">Kompilator języka C#, sama definiuje nie symboli lub makra używane w kodzie źródłowym; wszystkie definicje symboli muszą być zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="28113-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28113-117">C# `#define` nie zezwala na symbol należy podać wartości, tak jak w językach takich jak C++.</span><span class="sxs-lookup"><span data-stu-id="28113-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="28113-118">Na przykład `#define` nie można użyć, aby utworzyć makro lub aby zdefiniować stałą.</span><span class="sxs-lookup"><span data-stu-id="28113-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="28113-119">Jeśli potrzebujesz zdefiniować stałą, użyj `enum` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="28113-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="28113-120">Jeśli chcesz utworzyć makro styl C++, należy wziąć pod uwagę rozwiązań alternatywnych, takich jak typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="28113-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="28113-121">Ponieważ makra są bardzo podatne na błędy, C# nie zezwalają na ich użycia, ale zapewnia bezpieczniejszych alternatyw.</span><span class="sxs-lookup"><span data-stu-id="28113-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="28113-122">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28113-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="28113-123">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="28113-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="28113-124">Na **kompilacji** karty, wpisz symbol, który ma zostać określona w **symbole kompilacji warunkowej** pole.</span><span class="sxs-lookup"><span data-stu-id="28113-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="28113-125">Na przykład, jeśli używasz przykładu kodu, który następuje po prostu wpisz `xx` w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="28113-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="28113-126">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="28113-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28113-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="28113-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="28113-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28113-128">See also</span></span>

- [<span data-ttu-id="28113-129">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="28113-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="28113-130">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="28113-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
