---
title: DirectCast, operator
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 96cb2082d59373deb34d6894270205b7c1045850
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371521"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast — Operator (Visual Basic)
Wprowadza operację konwersji typu opartą na dziedziczeniu lub implementacji.  
  
## <a name="remarks"></a>Uwagi  
 `DirectCast`Program nie korzysta z Visual Basic procedur pomocniczych w czasie wykonywania dla konwersji, dlatego może zapewnić nieco lepszą wydajność niż `CType` podczas konwertowania na i z typu danych `Object` .  
  
 Użyj `DirectCast` słowa kluczowego podobnego do sposobu używania [funkcji CType](../functions/ctype-function.md) i słowa kluczowego [operatora TryCast](trycast-operator.md) . Możesz podać wyrażenie jako pierwszy argument i typ, aby przekonwertować go na jako drugi argument. `DirectCast`wymaga dziedziczenia lub relacji implementacji między typami danych dwóch argumentów. Oznacza to, że jeden typ musi dziedziczyć po lub zaimplementować inne.  
  
## <a name="errors-and-failures"></a>Błędy i błędy  
 `DirectCast`generuje błąd kompilatora, jeśli wykryje, że nie istnieje relacja dziedziczenia lub implementacji. Ale brak błędu kompilatora nie gwarantuje pomyślnej konwersji. Jeśli żądana konwersja jest zawężana, może się nie powieść w czasie wykonywania. W takim przypadku środowisko uruchomieniowe zgłosi <xref:System.InvalidCastException> błąd.  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Porównanie słów kluczowych konwersji typu jest następujące.  
  
|Słowo kluczowe|Typy danych|Relacja argumentu|Niepowodzenie czasu wykonywania|  
|---|---|---|---|  
|[CType — Funkcja](../functions/ctype-function.md)|Wszystkie typy danych|Konwersja rozszerzająca lub zawężania musi być zdefiniowana między dwoma typami danych|Generuje<xref:System.InvalidCastException>|  
|`DirectCast`|Wszystkie typy danych|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Generuje<xref:System.InvalidCastException>|  
|[TryCast, operator](trycast-operator.md)|Tylko typy referencyjne|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Zwraca wartość [Nothing](../nothing.md)|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje dwa zastosowania `DirectCast` , jeden, który zakończy się niepowodzeniem w czasie wykonywania.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 W poprzednim przykładzie typem czasu wykonywania `q` jest `Double` . `CType`powiedzie się `Double` , ponieważ można przekonwertować na `Integer` . Jednak pierwsze `DirectCast` kończy się niepowodzeniem w czasie wykonywania, ponieważ typ czasu wykonywania nie `Double` ma relacji dziedziczenia z `Integer` , chociaż istnieje konwersja. Sekunda `DirectCast` kończy się pomyślnie, ponieważ konwertuje typ <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control> , z którego <xref:System.Windows.Forms.Form> dziedziczy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
