---
title: Mid — instrukcja (Visual Basic)
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
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581475"
---
# <a name="mid-statement"></a>Mid — Instrukcja
Zastępuje określoną liczbę znaków w zmiennej `String` znakami z innego ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Części  
 `Target`  
 Wymagany. Nazwa zmiennej `String` do zmodyfikowania.  
  
 `Start`  
 Wymagany. wyrażenie `Integer`. Pozycja znaku w `Target`, w którym rozpoczyna się zastępowanie tekstu. `Start` używa indeksu jednego z nich.  
  
 `Length`  
 Opcjonalny. wyrażenie `Integer`. Liczba znaków do zastąpienia. W przypadku pominięcia zostanie użyta cała `String`.  
  
 `StringExpression`  
 Wymagany. wyrażenie `String`, które zastępuje część `Target`.  
  
## <a name="exceptions"></a>Wyjątki  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 lub `Length` < 0.|  
  
## <a name="remarks"></a>Uwagi  
 Liczba zastąpionych znaków jest zawsze mniejsza lub równa liczbie znaków w `Target`.  
  
 Visual Basic zawiera funkcję <xref:Microsoft.VisualBasic.Strings.Mid%2A> i instrukcję `Mid`. Te elementy działają na określonej liczbie znaków w ciągu, ale funkcja `Mid` zwraca znaki, a instrukcja `Mid` zastępuje znaki. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> Instrukcja `MidB` wcześniejszych wersji Visual Basic zastępuje podciąg w bajtach, a nie znaki. Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS). Wszystkie ciągi Visual Basic są w formacie Unicode, a `MidB` nie jest już obsługiwane.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używamy instrukcji `Mid`, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Moduł:** `Strings`  
  
 **Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Wprowadzenie do ciągów w Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
