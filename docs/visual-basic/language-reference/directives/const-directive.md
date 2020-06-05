---
title: '#Const, dyrektywa'
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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415469"
---
# <a name="const-directive"></a><span data-ttu-id="50eb5-102">#Const — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="50eb5-102">#Const Directive</span></span>

<span data-ttu-id="50eb5-103">Definiuje warunkowe stałe kompilatora dla Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="50eb5-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50eb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50eb5-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="50eb5-105">Części</span><span class="sxs-lookup"><span data-stu-id="50eb5-105">Parts</span></span>  

 `constname`  
 <span data-ttu-id="50eb5-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="50eb5-106">Required.</span></span> <span data-ttu-id="50eb5-107">Nazwa zdefiniowanej stałej.</span><span class="sxs-lookup"><span data-stu-id="50eb5-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="50eb5-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="50eb5-108">Required.</span></span> <span data-ttu-id="50eb5-109">Literał, inna warunkowa stała kompilatora lub dowolna kombinacja, która zawiera wszystkie lub wszystkie operatory arytmetyczne lub logiczne z wyjątkiem `Is` .</span><span class="sxs-lookup"><span data-stu-id="50eb5-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50eb5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50eb5-110">Remarks</span></span>  

 <span data-ttu-id="50eb5-111">Warunkowe stałe kompilatora są zawsze prywatne dla pliku, w którym się znajdują.</span><span class="sxs-lookup"><span data-stu-id="50eb5-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="50eb5-112">Nie można utworzyć publicznych stałych kompilatora przy użyciu `#Const` dyrektywy; można je utworzyć tylko w interfejsie użytkownika lub za pomocą `/define` opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="50eb5-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="50eb5-113">W programie można używać tylko warunkowych stałych kompilatora i literałów `expression` .</span><span class="sxs-lookup"><span data-stu-id="50eb5-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="50eb5-114">Użycie stałej standardowej zdefiniowanej z `Const` powodu błędu.</span><span class="sxs-lookup"><span data-stu-id="50eb5-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="50eb5-115">Odwrotnie, można użyć stałych zdefiniowanych ze `#Const` słowem kluczowym tylko dla kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="50eb5-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="50eb5-116">Stałe mogą być również niezdefiniowane, w takim przypadku mają wartość `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="50eb5-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50eb5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="50eb5-117">Example</span></span>  

 <span data-ttu-id="50eb5-118">Ten przykład używa `#Const` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="50eb5-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="50eb5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50eb5-119">See also</span></span>

- [<span data-ttu-id="50eb5-120">-Definiuj (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50eb5-120">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="50eb5-121">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="50eb5-121">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="50eb5-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="50eb5-122">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="50eb5-123">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="50eb5-123">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="50eb5-124">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="50eb5-124">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
