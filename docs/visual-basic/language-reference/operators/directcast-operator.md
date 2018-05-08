---
title: DirectCast — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 534e94ecc0a394caa2865c2da754ad8f4dbc6f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="directcast-operator-visual-basic"></a>DirectCast — Operator (Visual Basic)
Wprowadza operację konwersji typu na podstawie dziedziczenia lub wdrożenia.  
  
## <a name="remarks"></a>Uwagi  
 `DirectCast` nie używa języka Visual Basic pomocnika czasu wykonywania procedury konwersji, więc może ona nieco większą wydajność niż `CType` podczas konwersji z typu danych i `Object`.  
  
 Możesz użyć `DirectCast` — słowo kluczowe podobny do sposobu korzystania z [CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md) i [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) — słowo kluczowe. Należy podać wyrażenie jako pierwszego argumentu oraz typ konwertować jako drugi argument. `DirectCast` wymaga relacji dziedziczenia lub wykonania między dwa argumenty typów danych. Oznacza to, że jeden typ musi dziedziczyć lub implementować innych.  
  
## <a name="errors-and-failures"></a>Błędów i niepowodzeń  
 `DirectCast` generuje błąd kompilatora, jeśli wykryje, że żadna dziedziczenia lub implementacji relacja nie istnieje. Jednak brak wystąpi błąd kompilatora nie gwarantuje pomyślne konwersji. Jeśli żądany konwersja jest zawężenie, może nie działać w czasie wykonywania. W takim przypadku zgłasza wyjątek środowiska uruchomieniowego <xref:System.InvalidCastException> błędu.  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Poniżej przedstawiono porównanie słowa kluczowe konwersji typu.  
  
|Słowo kluczowe|Typy danych|Argument relacji|Błąd czasu wykonywania|  
|---|---|---|---|  
|[Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Wszystkie typy danych|Rozszerzanie i zwężanie konwersji muszą być zdefiniowane między dwoma typami|Zgłasza wyjątek <xref:System.InvalidCastException>|  
|`DirectCast`|Wszystkie typy danych|Jeden typ musi dziedziczyć lub implementować typ innych|Zgłasza wyjątek <xref:System.InvalidCastException>|  
|[Operator TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Tylko typy odwołań|Jeden typ musi dziedziczyć lub implementować typ innych|Zwraca [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano dwa zastosowania `DirectCast`, taki, który nie powiedzie się w czasie wykonywania i jedną, zakończy się pomyślnie.  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 W powyższym przykładzie typu czasu wykonywania `q` jest `Double`. `CType` powiedzie się, ponieważ `Double` może zostać przekonwertowany na `Integer`. Jednak pierwszy `DirectCast` zakończy się niepowodzeniem w czasie wykonywania, ponieważ typ środowiska wykonawczego `Double` nie ma żadnych relacji dziedziczenia z `Integer`, nawet jeśli istnieje konwersji. Drugi `DirectCast` powiedzie się, ponieważ są konwertowane typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control>, z którego <xref:System.Windows.Forms.Form> dziedziczy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
