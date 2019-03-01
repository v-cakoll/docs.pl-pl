---
title: '##Const — dyrektywa (Visual Basic)'
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
ms.openlocfilehash: fb937a5a9d4688730085829350cb20172db50e97
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967051"
---
# <a name="const-directive"></a><span data-ttu-id="b235e-102">#Const — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="b235e-102">#Const Directive</span></span>
<span data-ttu-id="b235e-103">Definiuje stałe warunkowe kompilatora dla języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b235e-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b235e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b235e-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b235e-105">Części</span><span class="sxs-lookup"><span data-stu-id="b235e-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="b235e-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b235e-106">Required.</span></span> <span data-ttu-id="b235e-107">Nazwa — stała definiowanego.</span><span class="sxs-lookup"><span data-stu-id="b235e-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="b235e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b235e-108">Required.</span></span> <span data-ttu-id="b235e-109">Literał, inne stałe warunkowe kompilatora lub dowolną kombinację, który zawiera dowolnych lub wszystkich operatorów arytmetycznych lub logiczne, z wyjątkiem `Is`.</span><span class="sxs-lookup"><span data-stu-id="b235e-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b235e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b235e-110">Remarks</span></span>  
 <span data-ttu-id="b235e-111">Warunkowe stałe kompilatora są zawsze prywatne dla pliku, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b235e-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="b235e-112">Nie można utworzyć stałe kompilatora publicznych, przy użyciu `#Const` dyrektywę; można je utworzyć, tylko w interfejsie użytkownika lub za pomocą `/define` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b235e-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="b235e-113">Można użyć tylko warunkowe stałe kompilatora i literały w `expression`.</span><span class="sxs-lookup"><span data-stu-id="b235e-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="b235e-114">Przy użyciu standardowych stałą zdefiniowane za pomocą `Const` powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="b235e-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="b235e-115">Z drugiej strony, można użyć stałe zdefiniowane za pomocą `#Const` — słowo kluczowe tylko w przypadku kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="b235e-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="b235e-116">Stałe również może być niezdefiniowana, w którym to przypadku mają wartość `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b235e-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b235e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="b235e-117">Example</span></span>  
 <span data-ttu-id="b235e-118">Dyrektywa `#Const` została użyta w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b235e-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b235e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b235e-119">See also</span></span>
- [<span data-ttu-id="b235e-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b235e-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="b235e-121">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="b235e-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="b235e-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b235e-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="b235e-123">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="b235e-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="b235e-124">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="b235e-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
