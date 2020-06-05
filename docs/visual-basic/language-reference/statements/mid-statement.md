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
ms.openlocfilehash: 90408fd8a8cfc9b74c8422d0571d61f8534403f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404457"
---
# <a name="mid-statement"></a><span data-ttu-id="49e95-102">Mid — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="49e95-102">Mid Statement</span></span>
<span data-ttu-id="49e95-103">Zastępuje określoną liczbę znaków w zmiennej znakami `String` z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e95-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e95-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49e95-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="49e95-105">Części</span><span class="sxs-lookup"><span data-stu-id="49e95-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="49e95-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="49e95-106">Required.</span></span> <span data-ttu-id="49e95-107">Nazwa `String` zmiennej do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="49e95-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="49e95-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="49e95-108">Required.</span></span> <span data-ttu-id="49e95-109">`Integer`wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49e95-109">`Integer` expression.</span></span> <span data-ttu-id="49e95-110">Pozycja znaku w `Target` miejscu, w którym rozpoczyna się zastępowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="49e95-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="49e95-111">`Start`używa indeksu jednego.</span><span class="sxs-lookup"><span data-stu-id="49e95-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="49e95-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="49e95-112">Optional.</span></span> <span data-ttu-id="49e95-113">`Integer`wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49e95-113">`Integer` expression.</span></span> <span data-ttu-id="49e95-114">Liczba znaków do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="49e95-114">Number of characters to replace.</span></span> <span data-ttu-id="49e95-115">W przypadku pominięcia `String` zostanie użyta wartość wszystkie.</span><span class="sxs-lookup"><span data-stu-id="49e95-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="49e95-116">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="49e95-116">Required.</span></span> <span data-ttu-id="49e95-117">`String`wyrażenie, które zastępuje część elementu `Target` .</span><span class="sxs-lookup"><span data-stu-id="49e95-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="49e95-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="49e95-118">Exceptions</span></span>  
  
|<span data-ttu-id="49e95-119">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="49e95-119">Exception type</span></span>|<span data-ttu-id="49e95-120">Warunek</span><span class="sxs-lookup"><span data-stu-id="49e95-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="49e95-121">`Start`<= 0 lub `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="49e95-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49e95-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49e95-122">Remarks</span></span>  
 <span data-ttu-id="49e95-123">Liczba zastąpionych znaków jest zawsze mniejsza lub równa liczbie znaków w `Target` .</span><span class="sxs-lookup"><span data-stu-id="49e95-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="49e95-124">Visual Basic ma <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkcję i `Mid` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="49e95-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="49e95-125">Te elementy działają na określonej liczbie znaków w ciągu, ale `Mid` Funkcja zwraca znaki, gdy `Mid` instrukcja zastępuje znaki.</span><span class="sxs-lookup"><span data-stu-id="49e95-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="49e95-126">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="49e95-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49e95-127">`MidB`Instrukcja wcześniejszych wersji Visual Basic zastępuje podciąg w bajtach, a nie znaki.</span><span class="sxs-lookup"><span data-stu-id="49e95-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="49e95-128">Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS).</span><span class="sxs-lookup"><span data-stu-id="49e95-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="49e95-129">Wszystkie ciągi Visual Basic są w formacie Unicode i `MidB` nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="49e95-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49e95-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="49e95-130">Example</span></span>  
 <span data-ttu-id="49e95-131">W tym przykładzie używa `Mid` instrukcji, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e95-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="49e95-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49e95-132">Requirements</span></span>  
 <span data-ttu-id="49e95-133">**Przestrzeń nazw:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="49e95-133">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="49e95-134">**Moduł:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="49e95-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="49e95-135">**Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="49e95-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e95-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49e95-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="49e95-137">Ciągi</span><span class="sxs-lookup"><span data-stu-id="49e95-137">Strings</span></span>](../../programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="49e95-138">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49e95-138">Introduction to Strings in Visual Basic</span></span>](../../programming-guide/language-features/strings/introduction-to-strings.md)
