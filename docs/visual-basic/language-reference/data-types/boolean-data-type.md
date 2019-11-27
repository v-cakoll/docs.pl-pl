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
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347847"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean Data Type (Visual Basic)

Przechowuje wartości, które mogą być tylko `True` lub `False`. Słowa kluczowe `True` i `False` odpowiadają dwóm stanom `Boolean` zmiennych.  
  
## <a name="remarks"></a>Uwagi  

 Użyj [typu danych Boolean (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) , aby zawierać wartości dwustanowe, takie jak true/false, yes/no lub on/off.  
  
 Wartość domyślna `Boolean` jest `False`.  
  
 wartości `Boolean` nie są przechowywane jako liczby, a przechowywane wartości nie mają być równoważne z liczbami. Nigdy nie należy pisać kodu, który opiera się na odpowiednich wartościach liczbowych dla `True` i `False`. Jeśli to możliwe, należy ograniczyć użycie zmiennych `Boolean` do wartości logicznych, dla których zostały zaprojektowane.  
  
## <a name="type-conversions"></a>Konwersje typu  

 Gdy Visual Basic konwertuje wartości liczbowe typu danych na `Boolean`, 0 staje się `False` i wszystkie pozostałe wartości stają się `True`. Gdy Visual Basic konwertuje wartości `Boolean` na typy liczbowe, `False` staje się 0, a `True` staje się-1.  
  
 Podczas konwertowania wartości `Boolean` i liczbowych typów danych, należy pamiętać, że metody konwersji .NET Framework nie zawsze generują te same wyniki, co w przypadku słów kluczowych konwersji Visual Basic. Dzieje się tak, ponieważ konwersja Visual Basic zachowuje zachowanie zgodne z poprzednimi wersjami. Aby uzyskać więcej informacji, zobacz "typ Boolean nie jest dokładnie konwertowany na typ liczbowy" w temacie [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Liczby ujemne.** `Boolean` nie jest typem liczbowym i nie może reprezentować wartości ujemnej. W każdym przypadku nie należy używać `Boolean` do przechowywania wartości liczbowych.  
  
- **Znaki typu.** `Boolean` nie ma znaku typu literału lub typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Boolean?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  

 W poniższym przykładzie `runningVB` jest zmienną `Boolean`, która przechowuje proste ustawienie tak/nie.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Boolean?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
