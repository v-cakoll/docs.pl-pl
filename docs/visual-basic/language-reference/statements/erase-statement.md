---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="a2d1b-102">Erase — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2d1b-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="a2d1b-103">Używane do zwalniania zmiennych tablicowych i cofnięcia przydzielenia pamięci używanej dla elementów.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2d1b-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="a2d1b-105">Części</span><span class="sxs-lookup"><span data-stu-id="a2d1b-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="a2d1b-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-106">Required.</span></span> <span data-ttu-id="a2d1b-107">Lista zmiennych tablicowych usunięcie.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-107">List of array variables to be erased.</span></span> <span data-ttu-id="a2d1b-108">Wiele zmiennych są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d1b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2d1b-109">Remarks</span></span>  
 <span data-ttu-id="a2d1b-110">`Erase` Instrukcja może wystąpić tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="a2d1b-111">Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasę lub moduł.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="a2d1b-112">`Erase` Instrukcja jest odpowiednikiem przypisywanie `Nothing` do każdej zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2d1b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2d1b-113">Example</span></span>  
 <span data-ttu-id="a2d1b-114">W poniższym przykładzie użyto `Erase` instrukcji, aby wyczyścić dwiema tablicami i zwolnić pamięć, ich (1000 i 100 elementów magazynu odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="a2d1b-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="a2d1b-115">`ReDim` Instrukcji następnie przypisuje nowego wystąpienia tablicy tablicą trójwymiarową.</span><span class="sxs-lookup"><span data-stu-id="a2d1b-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a2d1b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2d1b-116">See Also</span></span>  
 [<span data-ttu-id="a2d1b-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="a2d1b-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="a2d1b-118">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a2d1b-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
