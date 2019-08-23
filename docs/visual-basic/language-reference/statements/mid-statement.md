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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963551"
---
# <a name="mid-statement"></a>Mid — Instrukcja
Zastępuje określoną liczbę znaków w `String` zmiennej znakami z innego ciągu.  
  
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
 Wymagany. `String` Nazwa zmiennej do zmodyfikowania.  
  
 `Start`  
 Wymagany. `Integer`wyrażenia. Pozycja znaku w `Target` miejscu, w którym rozpoczyna się zastępowanie tekstu. `Start`używa indeksu jednego.  
  
 `Length`  
 Opcjonalny. `Integer`wyrażenia. Liczba znaków do zastąpienia. W przypadku pominięcia `String` zostanie użyta wartość wszystkie.  
  
 `StringExpression`  
 Wymagane. `String`wyrażenie, które zastępuje część `Target`elementu.  
  
## <a name="exceptions"></a>Wyjątki  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 lub `Length` < 0.|  
  
## <a name="remarks"></a>Uwagi  
 Liczba zastąpionych znaków jest zawsze mniejsza lub równa liczbie znaków w `Target`.  
  
 Visual Basic ma <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkcję `Mid` i instrukcję. Te elementy działają na określonej liczbie znaków w ciągu, ale `Mid` funkcja zwraca znaki, `Mid` gdy instrukcja zastępuje znaki. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> `MidB` Instrukcja wcześniejszych wersji Visual Basic zastępuje podciąg w bajtach, a nie znaki. Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS). Wszystkie ciągi Visual Basic są w formacie Unicode i `MidB` nie są już obsługiwane.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `Mid` instrukcji, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Wymagania  
 **Obszaru** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Moduł:** `Strings`  
  
 **Hamulc** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Wprowadzenie do ciągów w Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
