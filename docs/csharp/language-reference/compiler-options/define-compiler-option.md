---
title: -define (C# opcje kompilatora)
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
ms.openlocfilehash: d56907493ed24e2ea9fa6568af7441fc81ba1a78
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606951"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="d12a7-102">-define (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="d12a7-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="d12a7-103">Opcja **-define** definiuje `name` jako symbol we wszystkich plikach kodu źródłowego tego programu.</span><span class="sxs-lookup"><span data-stu-id="d12a7-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d12a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d12a7-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d12a7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d12a7-105">Arguments</span></span>  
 <span data-ttu-id="d12a7-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="d12a7-106">`name`, `name2`</span></span>  
 <span data-ttu-id="d12a7-107">Nazwa co najmniej jednego symbolu, który ma zostać zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d12a7-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d12a7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d12a7-108">Remarks</span></span>  
 <span data-ttu-id="d12a7-109">Opcja **-define** ma ten sam skutek jak użycie dyrektywy preprocesora [#define](../preprocessor-directives/preprocessor-define.md) , z wyjątkiem tego, że opcja kompilatora obowiązuje dla wszystkich plików w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d12a7-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="d12a7-110">Symbol pozostaje zdefiniowany w pliku źródłowym do momentu usunięcia definicji [#undef](../preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="d12a7-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="d12a7-111">W przypadku użycia opcji `#undef` -define dyrektywa w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d12a7-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="d12a7-112">Możesz użyć symboli utworzonych przez tę opcję z [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)i [#endif](../preprocessor-directives/preprocessor-endif.md) , aby warunkowo kompilować pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="d12a7-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="d12a7-113">**-d** jest krótką formą **-define**.</span><span class="sxs-lookup"><span data-stu-id="d12a7-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="d12a7-114">Można zdefiniować wiele symboli z **-Definiuj** przy użyciu średnika lub przecinka do oddzielenia nazw symboli.</span><span class="sxs-lookup"><span data-stu-id="d12a7-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="d12a7-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d12a7-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="d12a7-116">Sam C# kompilator definiuje nie symboli ani makr, których można użyć w kodzie źródłowym; wszystkie definicje symboli muszą być zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d12a7-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d12a7-117">Nie zezwala symbolowi na podaną wartość, jak w językach, takich jak C++ C# `#define`</span><span class="sxs-lookup"><span data-stu-id="d12a7-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="d12a7-118">Na przykład `#define` nie można użyć do utworzenia makra lub zdefiniowania stałej.</span><span class="sxs-lookup"><span data-stu-id="d12a7-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="d12a7-119">Jeśli musisz zdefiniować stałą, użyj `enum` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d12a7-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="d12a7-120">Jeśli chcesz utworzyć makro C++ stylu, weź pod uwagę alternatywy, takie jak typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="d12a7-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="d12a7-121">Ponieważ makra są wielowątkowy bardzo podatne na błędy, C# nie zezwalają na ich użycie, ale zapewniają bezpieczniejsze alternatywy.</span><span class="sxs-lookup"><span data-stu-id="d12a7-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d12a7-122">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d12a7-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d12a7-123">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="d12a7-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d12a7-124">Na karcie **kompilacja** wpisz symbol, który ma być zdefiniowany w polu **symbole kompilacji warunkowej** .</span><span class="sxs-lookup"><span data-stu-id="d12a7-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="d12a7-125">Na przykład, jeśli używasz poniższego przykładu kodu, po prostu wpisz `xx` w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="d12a7-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="d12a7-126">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="d12a7-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d12a7-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d12a7-127">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d12a7-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d12a7-128">See also</span></span>

- [<span data-ttu-id="d12a7-129">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d12a7-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d12a7-130">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d12a7-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
