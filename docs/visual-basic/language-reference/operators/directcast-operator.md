---
title: Operator DirectCast
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 8ea29b80cf27bbb2c21a8cebbfaa0a294e05f11d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331307"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast — Operator (Visual Basic)
Wprowadza operację konwersji typu opartą na dziedziczeniu lub implementacji.  
  
## <a name="remarks"></a>Uwagi  
 `DirectCast` nie używa procedur pomocnika w czasie wykonywania Visual Basic do konwersji, dlatego może zapewnić nieco lepszą wydajność niż `CType` podczas konwertowania na i z `Object`typu danych.  
  
 Użyj słowa kluczowego `DirectCast` podobnego do sposobu używania [funkcji CType](../../../visual-basic/language-reference/functions/ctype-function.md) i słowa kluczowego [operatora TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) . Możesz podać wyrażenie jako pierwszy argument i typ, aby przekonwertować go na jako drugi argument. `DirectCast` wymaga dziedziczenia lub implementacji relacji między typami danych dwóch argumentów. Oznacza to, że jeden typ musi dziedziczyć po lub zaimplementować inne.  
  
## <a name="errors-and-failures"></a>Błędy i błędy  
 `DirectCast` generuje błąd kompilatora, jeśli wykryje, że nie istnieje relacja dziedziczenia lub implementacji. Ale brak błędu kompilatora nie gwarantuje pomyślnej konwersji. Jeśli żądana konwersja jest zawężana, może się nie powieść w czasie wykonywania. W takim przypadku środowisko uruchomieniowe zgłasza błąd <xref:System.InvalidCastException>.  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Porównanie słów kluczowych konwersji typu jest następujące.  
  
|Słowo kluczowe|Typy danych|Relacja argumentu|Niepowodzenie czasu wykonywania|  
|---|---|---|---|  
|[Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Wszystkie typy danych|Konwersja rozszerzająca lub zawężania musi być zdefiniowana między dwoma typami danych|Zgłasza <xref:System.InvalidCastException>|  
|`DirectCast`|Wszystkie typy danych|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Zgłasza <xref:System.InvalidCastException>|  
|[Operator TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Tylko typy referencyjne|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje dwa zastosowania `DirectCast`, jeden, który zakończy się niepowodzeniem w czasie wykonywania, i taki, który się powiódł.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 W poprzednim przykładzie typ `q` czasu wykonywania jest `Double`. `CType` się powiedzie, ponieważ `Double` można przekonwertować na `Integer`. Jednak pierwsze `DirectCast` nie powiedzie się w czasie wykonywania, ponieważ typ czasu wykonywania `Double` nie ma relacji dziedziczenia z `Integer`, nawet jeśli istnieje konwersja. Druga `DirectCast` powiedzie się, ponieważ konwertuje z typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control>, z której <xref:System.Windows.Forms.Form> dziedziczy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
