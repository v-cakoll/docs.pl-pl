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
# <a name="mid-statement"></a>Mid — Instrukcja
Zastępuje określoną liczbę znaków w zmiennej znakami `String` z innego ciągu.  
  
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
 Wymagany. Nazwa `String` zmiennej do zmodyfikowania.  
  
 `Start`  
 Wymagany. `Integer`wyrażenia. Pozycja znaku w `Target` miejscu, w którym rozpoczyna się zastępowanie tekstu. `Start`używa indeksu jednego.  
  
 `Length`  
 Opcjonalny. `Integer`wyrażenia. Liczba znaków do zastąpienia. W przypadku pominięcia `String` zostanie użyta wartość wszystkie.  
  
 `StringExpression`  
 Wymagany. `String`wyrażenie, które zastępuje część elementu `Target` .  
  
## <a name="exceptions"></a>Wyjątki  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`<= 0 lub `Length` < 0.|  
  
## <a name="remarks"></a>Uwagi  
 Liczba zastąpionych znaków jest zawsze mniejsza lub równa liczbie znaków w `Target` .  
  
 Visual Basic ma <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkcję i `Mid` instrukcję. Te elementy działają na określonej liczbie znaków w ciągu, ale `Mid` Funkcja zwraca znaki, gdy `Mid` instrukcja zastępuje znaki. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> `MidB`Instrukcja wcześniejszych wersji Visual Basic zastępuje podciąg w bajtach, a nie znaki. Służy przede wszystkim do konwersji ciągów w aplikacjach z zestawami dwubajtowych znaków (znaków DBCS). Wszystkie ciągi Visual Basic są w formacie Unicode i `MidB` nie są już obsługiwane.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `Mid` instrukcji, aby zastąpić określoną liczbę znaków w zmiennej ciągu znakami z innego ciągu.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Moduł:**`Strings`  
  
 **Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Ciągi](../../programming-guide/language-features/strings/index.md)
- [Wprowadzenie do ciągów w Visual Basic](../../programming-guide/language-features/strings/introduction-to-strings.md)
