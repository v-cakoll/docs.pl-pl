---
title: "Erase — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="0fced-102">Erase — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fced-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="0fced-103">Używane do zwalniania zmiennych tablicowych i cofnięcia przydzielenia pamięci używanej dla elementów.</span><span class="sxs-lookup"><span data-stu-id="0fced-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fced-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fced-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="0fced-105">Części</span><span class="sxs-lookup"><span data-stu-id="0fced-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="0fced-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0fced-106">Required.</span></span> <span data-ttu-id="0fced-107">Lista zmiennych tablicowych usunięcie.</span><span class="sxs-lookup"><span data-stu-id="0fced-107">List of array variables to be erased.</span></span> <span data-ttu-id="0fced-108">Wiele zmiennych są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0fced-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fced-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fced-109">Remarks</span></span>  
 <span data-ttu-id="0fced-110">`Erase` Instrukcja może wystąpić tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="0fced-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="0fced-111">Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasę lub moduł.</span><span class="sxs-lookup"><span data-stu-id="0fced-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="0fced-112">`Erase` Instrukcja jest odpowiednikiem przypisywanie `Nothing` do każdej zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="0fced-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fced-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fced-113">Example</span></span>  
 <span data-ttu-id="0fced-114">W poniższym przykładzie użyto `Erase` instrukcji, aby wyczyścić dwiema tablicami i zwolnić pamięć, ich (1000 i 100 elementów magazynu odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="0fced-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="0fced-115">`ReDim` Instrukcji następnie przypisuje nowego wystąpienia tablicy tablicą trójwymiarową.</span><span class="sxs-lookup"><span data-stu-id="0fced-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0fced-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fced-116">See Also</span></span>  
 [<span data-ttu-id="0fced-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="0fced-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="0fced-118">ReDim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="0fced-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
