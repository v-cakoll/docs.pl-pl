---
title: Boolean, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374424"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean Data Type (Visual Basic)

Przechowuje wartości, które mogą być tylko `True` lub `False` . Słowa kluczowe `True` i `False` odpowiadają dwóm stanom `Boolean` zmiennych.  
  
## <a name="remarks"></a>Uwagi  

 Użyj [typu danych Boolean (Visual Basic)](boolean-data-type.md) , aby zawierać wartości dwustanowe, takie jak true/false, yes/no lub on/off.  
  
 Wartość domyślna `Boolean` to `False` .  
  
 `Boolean`wartości nie są przechowywane jako liczby, a przechowywane wartości nie są równoważne z liczbami. Nigdy nie należy pisać kodu, który opiera się na równoważnych wartościach liczbowych dla `True` i `False` . Zawsze, gdy jest to możliwe, należy ograniczyć użycie `Boolean` zmiennych do wartości logicznych, dla których zostały zaprojektowane.  
  
## <a name="type-conversions"></a>Konwersje typu  

 Gdy Visual Basic konwertuje wartości liczbowe typu danych na `Boolean` , wartość 0 staje się `False` i wszystkie inne wartości staną się `True` . Gdy Visual Basic konwertuje `Boolean` wartości na typy liczbowe, `False` staje się 0 i `True` zmieni się na-1.  
  
 Podczas konwertowania `Boolean` wartości i liczbowych typów danych należy pamiętać, że metody konwersji .NET Framework nie zawsze generują te same wyniki, co w przypadku słów kluczowych konwersji Visual Basic. Dzieje się tak, ponieważ konwersja Visual Basic zachowuje zachowanie zgodne z poprzednimi wersjami. Aby uzyskać więcej informacji, zobacz "typ Boolean nie jest dokładnie konwertowany na typ liczbowy" w temacie [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Liczby ujemne.** `Boolean`nie jest typem liczbowym i nie może reprezentować wartości ujemnej. W każdym przypadku nie należy używać `Boolean` do przechowywania wartości numerycznych.  
  
- **Znaki typu.** `Boolean`nie ma znaku typu literału lub znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Boolean?displayProperty=nameWithType> strukturą.  
  
## <a name="example"></a>Przykład  

 W poniższym przykładzie `runningVB` jest `Boolean` zmienną, która przechowuje proste ustawienie tak/nie.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Boolean?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType — Funkcja](../functions/ctype-function.md)
