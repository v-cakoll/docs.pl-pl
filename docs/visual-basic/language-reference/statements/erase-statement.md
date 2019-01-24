---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: cab3da4465b4671d203036c2d9bcd40662dc234a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522443"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="eb5f6-102">Erase — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb5f6-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="eb5f6-103">Służy do zwalniania zmiennych tablicy i cofania przydziału pamięci używanej dla ich elementów.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb5f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb5f6-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="eb5f6-105">Części</span><span class="sxs-lookup"><span data-stu-id="eb5f6-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="eb5f6-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-106">Required.</span></span> <span data-ttu-id="eb5f6-107">Lista zmiennych tablicy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-107">List of array variables to be erased.</span></span> <span data-ttu-id="eb5f6-108">W przypadku wielu zmiennych są one oddzielane przecinkami.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb5f6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb5f6-109">Remarks</span></span>  
 <span data-ttu-id="eb5f6-110">Instrukcja `Erase` może wystąpić tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="eb5f6-111">Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasy ani modułu.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="eb5f6-112">Instrukcja `Erase` jest równoważna z przypisywaniem wartości `Nothing` do każdej zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb5f6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb5f6-113">Example</span></span>  
 <span data-ttu-id="eb5f6-114">W poniższym przykładzie użyto instrukcji `Erase`, aby wyczyścić dwie tablice i zwolnić ich pamięć (odpowiednio 1000 i 100 elementów pamięci).</span><span class="sxs-lookup"><span data-stu-id="eb5f6-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="eb5f6-115">Następnie instrukcja `ReDim` przypisuje nową instancję tablicy do tablicy trójwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="eb5f6-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eb5f6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb5f6-116">See also</span></span>
- [<span data-ttu-id="eb5f6-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="eb5f6-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="eb5f6-118">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb5f6-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
