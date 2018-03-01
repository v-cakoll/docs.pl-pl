---
title: -Definiowanie (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 273437a4250a393274fa20ad4c02b61dce35ed34
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="c74f0-102">-Definiowanie (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c74f0-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="c74f0-103">**— Zdefiniuj** opcja definiuje `name` jako symbol w kodzie źródłowym wszystkie pliki programu.</span><span class="sxs-lookup"><span data-stu-id="c74f0-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c74f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c74f0-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c74f0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c74f0-105">Arguments</span></span>  
 <span data-ttu-id="c74f0-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="c74f0-106">`name`, `name2`</span></span>  
 <span data-ttu-id="c74f0-107">Nazwa jednego lub wielu symboli, które chcesz zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="c74f0-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c74f0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c74f0-108">Remarks</span></span>  
 <span data-ttu-id="c74f0-109">**— Zdefiniuj** opcja działa tak samo jak przy użyciu [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora z tą różnicą, że opcja kompilatora jest włączona dla wszystkich plików w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c74f0-109">The **-define** option has the same effect as using a [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="c74f0-110">Symbol pozostaje zdefiniowane w pliku źródłowym do [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym usuwa definicję.</span><span class="sxs-lookup"><span data-stu-id="c74f0-110">A symbol remains defined in a source file until an [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="c74f0-111">Jeśli używasz define — opcja, `#undef` dyrektywy w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c74f0-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="c74f0-112">Można użyć symboli utworzone przez tę opcję z [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), i [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) warunkowo skompilować plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="c74f0-112">You can use symbols created by this option with [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), and [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="c74f0-113">**-d** jest krótka forma **— Zdefiniuj**.</span><span class="sxs-lookup"><span data-stu-id="c74f0-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="c74f0-114">Można zdefiniować wiele symboli z **— Zdefiniuj** przy użyciu symbolu nazwy średnikami lub przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c74f0-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="c74f0-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c74f0-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="c74f0-116">Kompilator języka C#, sam definiuje nie symboli lub makra używane w kodzie źródłowym; wszystkie definicje symbolu muszą być zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c74f0-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c74f0-117">C# `#define` nie zezwala na symbolu, należy podać wartość, jak języków, takich jak C++.</span><span class="sxs-lookup"><span data-stu-id="c74f0-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="c74f0-118">Na przykład `#define` nie może służyć do tworzenia makr lub zdefiniuj stałą.</span><span class="sxs-lookup"><span data-stu-id="c74f0-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="c74f0-119">Jeśli musisz zdefiniować stałą, użyj `enum` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c74f0-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="c74f0-120">Jeśli chcesz utworzyć makro styl C++, należy wziąć pod uwagę rozwiązań alternatywnych, takich jak ogólne.</span><span class="sxs-lookup"><span data-stu-id="c74f0-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="c74f0-121">Ponieważ makra są bardzo podatne na błędy, C# nie zezwala na ich użycia, ale zapewnia bezpieczniejszych alternatyw.</span><span class="sxs-lookup"><span data-stu-id="c74f0-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c74f0-122">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c74f0-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c74f0-123">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="c74f0-123">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="c74f0-124">Na **kompilacji** , wpisz symbol, który ma być zdefiniowana w **symbole kompilacji warunkowej** pole.</span><span class="sxs-lookup"><span data-stu-id="c74f0-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="c74f0-125">Na przykład, jeśli używasz przykładowy kod, który następuje po prostu wpisz `xx` w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="c74f0-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="c74f0-126">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="c74f0-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c74f0-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="c74f0-127">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c74f0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c74f0-128">See Also</span></span>  
 [<span data-ttu-id="c74f0-129">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c74f0-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="c74f0-130">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c74f0-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
