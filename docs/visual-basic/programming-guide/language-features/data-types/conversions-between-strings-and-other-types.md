---
title: Konwertowanie między ciągami a innymi typami danych
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ae8f7c2159191536013fafd8bfd10fb9a93fb785
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394224"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)
Można przekonwertować wartość liczbową, `Boolean` lub datę/godzinę na `String` . Możesz również skonwertować w odwrotnym kierunku — od wartości ciągu na wartość numeryczną, `Boolean` lub `Date` — pod warunkiem, że zawartość ciągu może być interpretowana jako prawidłowa wartość docelowego typu danych. Jeśli nie, wystąpi błąd w czasie wykonywania.  
  
 Konwersje dla wszystkich tych przypisań, w obu kierunkach, zawężają konwersje. Należy użyć słów kluczowych konwersji typu (,,,,,,,,, `CBool` `CByte` `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` ,,,,, `CStr` `CUInt` `CULng` `CUShort` i `CType` ). <xref:Microsoft.VisualBasic.Strings.Format%2A>Funkcje i <xref:Microsoft.VisualBasic.Conversion.Val%2A> zapewniają dodatkową kontrolę nad konwersjami między ciągami i liczbami.  
  
 Jeśli zdefiniowano klasę lub strukturę, można zdefiniować operatory konwersji typów między `String` i typem klasy lub struktury. Aby uzyskać więcej informacji, zobacz [jak: definiowanie operatora konwersji](../procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Konwersja liczb na ciągi  
 Możesz użyć funkcji, `Format` Aby skonwertować liczbę do sformatowanego ciągu, który może zawierać nie tylko odpowiednie cyfry, ale także formatowanie symboli, takich jak znak waluty (na przykład `$` ), separatory tysięcy lub *symbole grupowania cyfr* (takie jak `,` ), oraz separator dziesiętny (na przykład `.` ). `Format`Program automatycznie używa odpowiednich symboli zgodnie z ustawieniami **opcji regionalnych** określonymi w **Panelu sterowania**systemu Windows.  
  
 Należy zauważyć, że operator łączenia ( `&` ) może przekonwertować liczbę na ciąg niejawnie, jak pokazano w poniższym przykładzie.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Konwersja ciągów na liczby  
 Możesz użyć funkcji, `Val` Aby jawnie skonwertować cyfry w ciągu na liczbę. `Val`odczytuje ciąg, dopóki nie napotka znaku innego niż cyfra, spacja, tabulator, wysuw wiersza lub kropki. Sekwencje "&O" i "&H" zmieniają podstawę systemu liczb i przerywają skanowanie. Dopóki nie zakończy się odczytywanie, program `Val` konwertuje wszystkie odpowiednie znaki na wartość liczbową. Na przykład poniższa instrukcja zwraca wartość `141.825` .  
  
 `Val("   14   1.825 miles")`  
  
 Gdy Visual Basic konwertuje ciąg na wartość liczbową, używa ustawień **opcji regionalnych** określonych w **Panelu sterowania** systemu Windows, aby interpretować separator tysięcy, separator dziesiętny i symbol waluty. Oznacza to, że konwersja może się powieść w ramach jednego ustawienia, ale nie do innego. Na przykład `"$14.20"` jest akceptowalny w ustawieniach regionalnych (Stany Zjednoczone) w języku angielskim, ale nie w ustawieniach regionalnych.  
  
## <a name="see-also"></a>Zobacz też

- [Konwersje plików w Visual Basic](type-conversions.md)
- [Rozszerzanie i zwężanie konwersji](widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](implicit-and-explicit-conversions.md)
- [Porady: konwertowanie obiektu do innego typu w Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Konwersje tablic](array-conversions.md)
- [Typy danych](../../../language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../language-reference/functions/type-conversion-functions.md)
- [Opracowywanie aplikacji globalnych i zlokalizowanych](/visualstudio/ide/globalizing-and-localizing-applications)
