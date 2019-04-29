---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638197"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="f9347-102">Erase — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9347-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="f9347-103">Służy do zwalniania zmiennych tablicy i cofania przydziału pamięci używanej dla ich elementów.</span><span class="sxs-lookup"><span data-stu-id="f9347-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9347-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9347-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="f9347-105">Części</span><span class="sxs-lookup"><span data-stu-id="f9347-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="f9347-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="f9347-106">Required.</span></span> <span data-ttu-id="f9347-107">Lista zmiennych tablicy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="f9347-107">List of array variables to be erased.</span></span> <span data-ttu-id="f9347-108">W przypadku wielu zmiennych są one oddzielane przecinkami.</span><span class="sxs-lookup"><span data-stu-id="f9347-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9347-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9347-109">Remarks</span></span>  
 <span data-ttu-id="f9347-110">Instrukcja `Erase` może wystąpić tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="f9347-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="f9347-111">Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasy ani modułu.</span><span class="sxs-lookup"><span data-stu-id="f9347-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="f9347-112">Instrukcja `Erase` jest równoważna z przypisywaniem wartości `Nothing` do każdej zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9347-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9347-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9347-113">Example</span></span>  
 <span data-ttu-id="f9347-114">W poniższym przykładzie użyto instrukcji `Erase`, aby wyczyścić dwie tablice i zwolnić ich pamięć (odpowiednio 1000 i 100 elementów pamięci).</span><span class="sxs-lookup"><span data-stu-id="f9347-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="f9347-115">Następnie instrukcja `ReDim` przypisuje nową instancję tablicy do tablicy trójwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="f9347-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="f9347-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9347-116">See also</span></span>

- [<span data-ttu-id="f9347-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="f9347-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="f9347-118">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9347-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
