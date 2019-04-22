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
ms.openlocfilehash: df83fd527612af1a6a4b8131ffa2643ef0d1d7dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818569"
---
# <a name="mid-statement"></a><span data-ttu-id="69801-102">Mid — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="69801-102">Mid Statement</span></span>
<span data-ttu-id="69801-103">Zamienia określoną liczbę znaków w `String` zmiennej znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="69801-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69801-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69801-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="69801-105">Części</span><span class="sxs-lookup"><span data-stu-id="69801-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="69801-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="69801-106">Required.</span></span> <span data-ttu-id="69801-107">Nazwa `String` zmiennej, do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="69801-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="69801-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="69801-108">Required.</span></span> <span data-ttu-id="69801-109">`Integer` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="69801-109">`Integer` expression.</span></span> <span data-ttu-id="69801-110">Znak na pozycji w `Target` gdzie rozpoczyna się zastępowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="69801-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="69801-111">`Start` używa indeksu liczonego od jednego.</span><span class="sxs-lookup"><span data-stu-id="69801-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="69801-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="69801-112">Optional.</span></span> <span data-ttu-id="69801-113">`Integer` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="69801-113">`Integer` expression.</span></span> <span data-ttu-id="69801-114">Liczba znaków do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="69801-114">Number of characters to replace.</span></span> <span data-ttu-id="69801-115">Jeśli argument jest pominięty, wszystkie `String` jest używany.</span><span class="sxs-lookup"><span data-stu-id="69801-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="69801-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="69801-116">Required.</span></span> <span data-ttu-id="69801-117">`String` wyrażenie, które zastępuje część `Target`.</span><span class="sxs-lookup"><span data-stu-id="69801-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="69801-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="69801-118">Exceptions</span></span>  
  
|<span data-ttu-id="69801-119">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="69801-119">Exception type</span></span>|<span data-ttu-id="69801-120">Warunek</span><span class="sxs-lookup"><span data-stu-id="69801-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="69801-121">`Start` < = 0 lub `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="69801-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69801-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69801-122">Remarks</span></span>  
 <span data-ttu-id="69801-123">Liczba znaków jest zawsze mniejsza niż liczba znaków w `Target`.</span><span class="sxs-lookup"><span data-stu-id="69801-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="69801-124">Visual Basic ma <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkcji i `Mid` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="69801-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="69801-125">Te elementy jednocześnie działać na określoną liczbę znaków w ciągu, ale `Mid` funkcja zwraca znaki podczas `Mid` instrukcji zastępuje znaki.</span><span class="sxs-lookup"><span data-stu-id="69801-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="69801-126">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="69801-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69801-127">`MidB` Instrukcji wcześniejszych wersji programu Visual Basic zastępuje podciąg w bajtach, a nie znaków.</span><span class="sxs-lookup"><span data-stu-id="69801-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="69801-128">Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS).</span><span class="sxs-lookup"><span data-stu-id="69801-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="69801-129">Wszystkie ciągi języka Visual Basic są w formacie Unicode, i `MidB` nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="69801-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69801-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="69801-130">Example</span></span>  
 <span data-ttu-id="69801-131">W tym przykładzie użyto `Mid` instrukcję, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="69801-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="69801-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69801-132">Requirements</span></span>  
 <span data-ttu-id="69801-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="69801-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="69801-134">**Moduł:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="69801-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="69801-135">**Zestaw:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69801-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69801-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69801-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="69801-137">Ciągi</span><span class="sxs-lookup"><span data-stu-id="69801-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="69801-138">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69801-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
