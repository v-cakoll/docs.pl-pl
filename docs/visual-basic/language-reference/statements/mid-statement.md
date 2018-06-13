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
ms.openlocfilehash: 90b805df902dcdfebe85421583dd54e9af04bec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602268"
---
# <a name="mid-statement"></a>Mid — Instrukcja
Zamienia określoną liczbę znaków w `String` zmiennej znakami z innego ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Części  
 `Target`  
 Wymagana. Nazwa `String` zmienną do zmodyfikowania.  
  
 `Start`  
 Wymagana. `Integer` Wyrażenie. Znak na pozycji w `Target` której rozpoczyna się zastępowanie tekstu. `Start` używa jednego indeksu.  
  
 `Length`  
 Opcjonalna. `Integer` Wyrażenie. Liczba znaków do zastąpienia. Pominięcie wszystkich `String` jest używany.  
  
 `StringExpression`  
 Wymagana. `String` wyrażenie, które zastępuje część `Target`.  
  
## <a name="exceptions"></a>Wyjątki  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 lub `Length` < 0.|  
  
## <a name="remarks"></a>Uwagi  
 Liczba znaków zawsze jest mniejsza niż liczba znaków w `Target`.  
  
 Visual Basic ma <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkcji i `Mid` instrukcji. Te elementy jednocześnie działać na określoną liczbę znaków w ciągu, ale `Mid` funkcja zwraca znaków podczas `Mid` instrukcji zastępuje znaki. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  `MidB` Instrukcji wcześniejszych wersji programu Visual Basic zastępuje podciąg w bajtach, zamiast znaków. Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS). Wszystkie ciągi Visual Basic są w formacie Unicode, i `MidB` nie jest już obsługiwana.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Mid` instrukcji, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Moduł:** `Strings`  
  
 **Zestaw:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [Ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Wprowadzenie do ciągów w Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
