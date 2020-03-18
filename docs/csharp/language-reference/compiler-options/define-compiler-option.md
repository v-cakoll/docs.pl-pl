---
title: -define (Opcje kompilatora C#)
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
ms.openlocfilehash: 4a3622b6acc8ebe9c590b01b67074ae59396fc34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173747"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="43db0-102">-define (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="43db0-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="43db0-103">Opcja **-define** definiuje `name` jako symbol we wszystkich plikach kodu źródłowego programu.</span><span class="sxs-lookup"><span data-stu-id="43db0-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43db0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43db0-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="43db0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="43db0-105">Arguments</span></span>  
 <span data-ttu-id="43db0-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="43db0-106">`name`, `name2`</span></span>  
 <span data-ttu-id="43db0-107">Nazwa jednego lub więcej symboli, które chcesz zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="43db0-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43db0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43db0-108">Remarks</span></span>  
 <span data-ttu-id="43db0-109">**Opcja -define** ma taki sam efekt jak przy użyciu #define dyrektywy preprocesora, z tą różnicą, że opcja kompilatora obowiązuje dla wszystkich plików w projekcie. [#define](../preprocessor-directives/preprocessor-define.md)</span><span class="sxs-lookup"><span data-stu-id="43db0-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="43db0-110">Symbol pozostaje zdefiniowany w pliku źródłowym, dopóki [#undef](../preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym nie usunie definicji.</span><span class="sxs-lookup"><span data-stu-id="43db0-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="43db0-111">Korzystając z opcji -define, `#undef` dyrektywa w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.</span><span class="sxs-lookup"><span data-stu-id="43db0-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="43db0-112">Symboli utworzonych przez tę opcję można używać za pomocą [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)i [#endif](../preprocessor-directives/preprocessor-endif.md) do warunkowego kompilowania plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="43db0-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="43db0-113">**-d** jest krótką formą **-define**.</span><span class="sxs-lookup"><span data-stu-id="43db0-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="43db0-114">Można zdefiniować wiele symboli za pomocą **-define** za pomocą średnika lub przecinka do oddzielania nazw symboli.</span><span class="sxs-lookup"><span data-stu-id="43db0-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="43db0-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="43db0-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="43db0-116">Kompilator Języka C# sam definiuje żadnych symboli lub makr, których można użyć w kodzie źródłowym; wszystkie definicje symboli muszą być zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="43db0-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43db0-117">C# `#define` nie zezwala na symbol, aby otrzymać wartość, jak w językach, takich jak C++.</span><span class="sxs-lookup"><span data-stu-id="43db0-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="43db0-118">Na przykład `#define` nie można użyć do utworzenia makra lub do zdefiniowania stałej.</span><span class="sxs-lookup"><span data-stu-id="43db0-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="43db0-119">Jeśli trzeba zdefiniować stałą, `enum` należy użyć zmiennej.</span><span class="sxs-lookup"><span data-stu-id="43db0-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="43db0-120">Jeśli chcesz utworzyć makro stylu C++, rozważ alternatywy, takie jak generycznych.</span><span class="sxs-lookup"><span data-stu-id="43db0-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="43db0-121">Ponieważ makra są notorycznie podatne na błędy, C# nie zezwala na ich użycie, ale zapewnia bezpieczniejsze alternatywy.</span><span class="sxs-lookup"><span data-stu-id="43db0-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="43db0-122">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43db0-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="43db0-123">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="43db0-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="43db0-124">Na **karcie Kompilacja** wpisz symbol, który ma być zdefiniowany w polu **Symbole kompilacji warunkowej.**</span><span class="sxs-lookup"><span data-stu-id="43db0-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="43db0-125">Na przykład jeśli używasz przykładu kodu, który `xx` następuje, wystarczy wpisać w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="43db0-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="43db0-126">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="43db0-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43db0-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="43db0-127">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43db0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43db0-128">See also</span></span>

- [<span data-ttu-id="43db0-129">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="43db0-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="43db0-130">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="43db0-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
