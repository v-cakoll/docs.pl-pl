---
title: Mid — Instrukcja
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
ms.openlocfilehash: eeef4c13743b75a3d5e61ac46afb94d9ea105b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348023"
---
# <a name="mid-statement"></a><span data-ttu-id="ad960-102">Mid — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ad960-102">Mid Statement</span></span>
<span data-ttu-id="ad960-103">Zastępuje określoną liczbę znaków w zmiennej `String` znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="ad960-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad960-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad960-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="ad960-105">Części</span><span class="sxs-lookup"><span data-stu-id="ad960-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="ad960-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ad960-106">Required.</span></span> <span data-ttu-id="ad960-107">Nazwa zmiennej `String` do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="ad960-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="ad960-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ad960-108">Required.</span></span> <span data-ttu-id="ad960-109">wyrażenie `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ad960-109">`Integer` expression.</span></span> <span data-ttu-id="ad960-110">Pozycja znaku w `Target`, w którym rozpoczyna się zastępowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="ad960-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="ad960-111">`Start` używa indeksu jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="ad960-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="ad960-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ad960-112">Optional.</span></span> <span data-ttu-id="ad960-113">wyrażenie `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ad960-113">`Integer` expression.</span></span> <span data-ttu-id="ad960-114">Liczba znaków do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="ad960-114">Number of characters to replace.</span></span> <span data-ttu-id="ad960-115">W przypadku pominięcia zostanie użyta cała `String`.</span><span class="sxs-lookup"><span data-stu-id="ad960-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="ad960-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ad960-116">Required.</span></span> <span data-ttu-id="ad960-117">wyrażenie `String`, które zastępuje część `Target`.</span><span class="sxs-lookup"><span data-stu-id="ad960-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="ad960-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ad960-118">Exceptions</span></span>  
  
|<span data-ttu-id="ad960-119">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="ad960-119">Exception type</span></span>|<span data-ttu-id="ad960-120">Warunek</span><span class="sxs-lookup"><span data-stu-id="ad960-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="ad960-121">`Start` < = 0 lub `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="ad960-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad960-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad960-122">Remarks</span></span>  
 <span data-ttu-id="ad960-123">Liczba zastąpionych znaków jest zawsze mniejsza lub równa liczbie znaków w `Target`.</span><span class="sxs-lookup"><span data-stu-id="ad960-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="ad960-124">Visual Basic zawiera funkcję <xref:Microsoft.VisualBasic.Strings.Mid%2A> i instrukcję `Mid`.</span><span class="sxs-lookup"><span data-stu-id="ad960-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="ad960-125">Te elementy działają na określonej liczbie znaków w ciągu, ale funkcja `Mid` zwraca znaki, podczas gdy instrukcja `Mid` zastępuje znaki.</span><span class="sxs-lookup"><span data-stu-id="ad960-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="ad960-126">Aby uzyskać więcej informacji, zobacz temat <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad960-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad960-127">Instrukcja `MidB` wcześniejszych wersji Visual Basic zastępuje podciąg w bajtach, a nie znaki.</span><span class="sxs-lookup"><span data-stu-id="ad960-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="ad960-128">Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS).</span><span class="sxs-lookup"><span data-stu-id="ad960-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="ad960-129">Wszystkie ciągi Visual Basic są w formacie Unicode, a `MidB` nie jest już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ad960-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad960-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad960-130">Example</span></span>  
 <span data-ttu-id="ad960-131">W tym przykładzie używamy instrukcji `Mid`, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="ad960-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="ad960-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad960-132">Requirements</span></span>  
 <span data-ttu-id="ad960-133">**Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ad960-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ad960-134">**Moduł:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="ad960-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="ad960-135">**Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="ad960-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad960-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad960-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="ad960-137">Ciągi</span><span class="sxs-lookup"><span data-stu-id="ad960-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="ad960-138">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad960-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
