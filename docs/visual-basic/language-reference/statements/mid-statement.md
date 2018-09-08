---
title: MID — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: a653e63ded04616b6b0c6bdfb26a0a673d9299fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209358"
---
# <a name="mid-statement"></a><span data-ttu-id="912f4-102">Mid — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="912f4-102">Mid Statement</span></span>
<span data-ttu-id="912f4-103">Zamienia określoną liczbę znaków w `String` zmiennej znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="912f4-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="912f4-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="912f4-105">Części</span><span class="sxs-lookup"><span data-stu-id="912f4-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="912f4-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="912f4-106">Required.</span></span> <span data-ttu-id="912f4-107">Nazwa `String` zmiennej, do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="912f4-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="912f4-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="912f4-108">Required.</span></span> <span data-ttu-id="912f4-109">`Integer` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="912f4-109">`Integer` expression.</span></span> <span data-ttu-id="912f4-110">Znak na pozycji w `Target` gdzie rozpoczyna się zastępowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="912f4-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="912f4-111">`Start` używa indeksu liczonego od jednego.</span><span class="sxs-lookup"><span data-stu-id="912f4-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="912f4-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="912f4-112">Optional.</span></span> <span data-ttu-id="912f4-113">`Integer` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="912f4-113">`Integer` expression.</span></span> <span data-ttu-id="912f4-114">Liczba znaków do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="912f4-114">Number of characters to replace.</span></span> <span data-ttu-id="912f4-115">Jeśli argument jest pominięty, wszystkie `String` jest używany.</span><span class="sxs-lookup"><span data-stu-id="912f4-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="912f4-116">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="912f4-116">Required.</span></span> <span data-ttu-id="912f4-117">`String` wyrażenie, które zastępuje część `Target`.</span><span class="sxs-lookup"><span data-stu-id="912f4-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="912f4-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="912f4-118">Exceptions</span></span>  
  
|<span data-ttu-id="912f4-119">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="912f4-119">Exception type</span></span>|<span data-ttu-id="912f4-120">Warunek</span><span class="sxs-lookup"><span data-stu-id="912f4-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="912f4-121">`Start` < = 0 lub `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="912f4-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="912f4-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="912f4-122">Remarks</span></span>  
 <span data-ttu-id="912f4-123">Liczba znaków jest zawsze mniejsza niż liczba znaków w `Target`.</span><span class="sxs-lookup"><span data-stu-id="912f4-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="912f4-124">Visual Basic ma <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkcji i `Mid` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="912f4-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="912f4-125">Te elementy jednocześnie działać na określoną liczbę znaków w ciągu, ale `Mid` funkcja zwraca znaki podczas `Mid` instrukcji zastępuje znaki.</span><span class="sxs-lookup"><span data-stu-id="912f4-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="912f4-126">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="912f4-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="912f4-127">`MidB` Instrukcji wcześniejszych wersji programu Visual Basic zastępuje podciąg w bajtach, a nie znaków.</span><span class="sxs-lookup"><span data-stu-id="912f4-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="912f4-128">Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS).</span><span class="sxs-lookup"><span data-stu-id="912f4-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="912f4-129">Wszystkie ciągi języka Visual Basic są w formacie Unicode, i `MidB` nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="912f4-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="912f4-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="912f4-130">Example</span></span>  
 <span data-ttu-id="912f4-131">W tym przykładzie użyto `Mid` instrukcję, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="912f4-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="912f4-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="912f4-132">Requirements</span></span>  
 <span data-ttu-id="912f4-133">**Przestrzeń nazw:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="912f4-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="912f4-134">**Moduł:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="912f4-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="912f4-135">**Zestaw:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912f4-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912f4-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="912f4-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="912f4-137">Ciągi</span><span class="sxs-lookup"><span data-stu-id="912f4-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="912f4-138">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="912f4-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
