---
title: -Definiowanie (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: d0a483e7a3c9e9863db39e89d655cf172c1e8c81
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834312"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="f2c56-102">-Definiowanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2c56-102">-define (Visual Basic)</span></span>
<span data-ttu-id="f2c56-103">Definiuje stałe warunkowe kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f2c56-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2c56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2c56-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2c56-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f2c56-105">Arguments</span></span>  
  
|<span data-ttu-id="f2c56-106">Termin</span><span class="sxs-lookup"><span data-stu-id="f2c56-106">Term</span></span>|<span data-ttu-id="f2c56-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="f2c56-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="f2c56-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f2c56-108">Required.</span></span> <span data-ttu-id="f2c56-109">Aby zdefiniować symbol.</span><span class="sxs-lookup"><span data-stu-id="f2c56-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="f2c56-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f2c56-110">Optional.</span></span> <span data-ttu-id="f2c56-111">Wartość do przypisania `symbol`.</span><span class="sxs-lookup"><span data-stu-id="f2c56-111">The value to assign `symbol`.</span></span> <span data-ttu-id="f2c56-112">Jeśli `value` jest ciągiem, muszą być ujęte przez sekwencje ukośnik odwrotny — cudzysłów (\\") zamiast znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="f2c56-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="f2c56-113">Jeśli nie określono wartości, a następnie jest traktowana jako wartość True.</span><span class="sxs-lookup"><span data-stu-id="f2c56-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2c56-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2c56-114">Remarks</span></span>  
 <span data-ttu-id="f2c56-115">`-define` Opcji obowiązuje, podobnie jak przy użyciu `#Const` dyrektywy preprocesora w pliku źródłowym, z wyjątkiem tego stałe zdefiniowane za pomocą `-define` były publiczne i zastosować do wszystkich plików w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f2c56-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="f2c56-116">Można użyć symboli utworzone przez tę opcję z `#If`... `Then`... `#Else` dyrektywy, aby warunkowo skompilować pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="f2c56-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="f2c56-117">`-d` jest to forma krótka `-define`.</span><span class="sxs-lookup"><span data-stu-id="f2c56-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="f2c56-118">Można zdefiniować wiele symboli z `-define` za pomocą przecinków do oddzielenia definicje symbolu.</span><span class="sxs-lookup"><span data-stu-id="f2c56-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="f2c56-119">Aby ustawić / define w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="f2c56-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f2c56-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f2c56-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f2c56-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f2c56-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f2c56-122">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="f2c56-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f2c56-123">3.  Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="f2c56-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="f2c56-124">4.  Zmodyfikuj wartość w **stałe niestandardowe** pole.</span><span class="sxs-lookup"><span data-stu-id="f2c56-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f2c56-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2c56-125">Example</span></span>  
 <span data-ttu-id="f2c56-126">Poniższy kod definiuje, a następnie używa dwóch warunkowe stałe kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f2c56-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="f2c56-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2c56-127">See also</span></span>

- [<span data-ttu-id="f2c56-128">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2c56-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f2c56-129">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="f2c56-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="f2c56-130">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="f2c56-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="f2c56-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f2c56-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
