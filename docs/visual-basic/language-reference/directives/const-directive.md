---
title: '#Const-dyrektywa'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: a3b3318f6b44f7d1798e08195be5aeb920b61c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588070"
---
# <a name="const-directive"></a><span data-ttu-id="7b7f3-102">#Const — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="7b7f3-102">#Const Directive</span></span>
<span data-ttu-id="7b7f3-103">Definiuje warunkowe stałe kompilatora Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b7f3-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="7b7f3-105">Części</span><span class="sxs-lookup"><span data-stu-id="7b7f3-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="7b7f3-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-106">Required.</span></span> <span data-ttu-id="7b7f3-107">Nazwa stała jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="7b7f3-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-108">Required.</span></span> <span data-ttu-id="7b7f3-109">Literał, inne warunkowego kompilatora stałej lub dowolnej kombinacji, która obejmuje dowolnych lub wszystkich operatorów arytmetycznych i logicznych z wyjątkiem `Is`.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b7f3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b7f3-110">Remarks</span></span>  
 <span data-ttu-id="7b7f3-111">Warunkowe stałe kompilatora są zawsze prywatne dla pliku, w jakiej widnieją.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="7b7f3-112">Nie można utworzyć stałe kompilatora publiczny przy użyciu `#Const` dyrektywy; tylko w interfejsie użytkownika lub można je utworzyć `/define` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="7b7f3-113">Można użyć tylko warunkowe stałe kompilatora i literały w `expression`.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="7b7f3-114">Przy użyciu standardowych stałą zdefiniowane z `Const` powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="7b7f3-115">Z drugiej strony, można użyć stałe zdefiniowane z `#Const` — słowo kluczowe tylko dla kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="7b7f3-116">Stałe również może być niezdefiniowana, w takim przypadku mają wartość `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b7f3-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b7f3-117">Example</span></span>  
 <span data-ttu-id="7b7f3-118">Dyrektywa `#Const` została użyta w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b7f3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b7f3-119">See Also</span></span>  
 [<span data-ttu-id="7b7f3-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b7f3-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="7b7f3-121">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="7b7f3-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="7b7f3-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7b7f3-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="7b7f3-123">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="7b7f3-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="7b7f3-124">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7b7f3-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
