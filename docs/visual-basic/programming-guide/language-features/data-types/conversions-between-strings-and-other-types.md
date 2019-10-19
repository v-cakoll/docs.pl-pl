---
title: Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: e1530c1772808249546b453294fc848c31c1e581
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582938"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)
Można przekonwertować wartość liczbową, `Boolean` lub daty/godziny na `String`. Możesz również skonwertować w odwrotnym kierunku — od wartości ciągu na liczbowy, `Boolean` lub `Date` — pod warunkiem, że zawartość ciągu może być interpretowana jako prawidłowa wartość docelowego typu danych. Jeśli nie, wystąpi błąd w czasie wykonywania.  
  
 Konwersje dla wszystkich tych przypisań, w obu kierunkach, zawężają konwersje. Należy użyć słów kluczowych konwersji typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, 0, 1, 2 , 3 i 4). Funkcje <xref:Microsoft.VisualBasic.Strings.Format%2A> i <xref:Microsoft.VisualBasic.Conversion.Val%2A> zapewniają dodatkową kontrolę nad konwersjami między ciągami i liczbami.  
  
 Jeśli zdefiniowano klasę lub strukturę, można zdefiniować operatory konwersji typu między `String` i typ klasy lub struktury. Aby uzyskać więcej informacji, zobacz [jak: definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Konwersja liczb na ciągi  
 Można użyć funkcji `Format`, aby skonwertować liczbę do sformatowanego ciągu, który może zawierać nie tylko odpowiednie cyfry, ale także formatowanie symboli, takich jak znak waluty (na przykład `$`), separatory tysięcy lub *symbole grupowania cyfr* (takie jak @no __t_3) i separator dziesiętny (na przykład `.`). `Format` automatycznie używa odpowiednich symboli zgodnie z ustawieniami **opcji regionalnych** określonymi w **Panelu sterowania**systemu Windows.  
  
 Należy zauważyć, że operator łączenia (`&`) może przekonwertować liczbę na ciąg niejawnie, jak pokazano w poniższym przykładzie.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Konwersja ciągów na liczby  
 Za pomocą funkcji `Val` można jawnie skonwertować cyfry w ciągu na liczbę. `Val` odczytuje ciąg, dopóki nie napotka znaku innego niż cyfra, spacja, tabulator, wysuw wiersza lub kropki. Sekwencje "& O" i "& H" zmieniają podstawę systemu liczb i przerywają skanowanie. Dopóki nie przestanie się odczytywania, `Val` konwertuje wszystkie odpowiednie znaki na wartość liczbową. Na przykład poniższa instrukcja zwraca wartość `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Gdy Visual Basic konwertuje ciąg na wartość liczbową, używa ustawień **opcji regionalnych** określonych w **Panelu sterowania** systemu Windows, aby interpretować separator tysięcy, separator dziesiętny i symbol waluty. Oznacza to, że konwersja może się powieść w ramach jednego ustawienia, ale nie do innego. Na przykład `"$14.20"` jest akceptowalny dla ustawień regionalnych (Stany Zjednoczone) w języku angielskim, ale nie w ustawieniach regionalnych.  
  
## <a name="see-also"></a>Zobacz także

- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Instrukcje: konwertowanie obiektu na inny typ w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
