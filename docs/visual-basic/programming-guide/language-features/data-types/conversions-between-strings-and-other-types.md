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
ms.openlocfilehash: 1e42fca7800a76cab10fd60058e34d31ae8b8830
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821664"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)
Możesz przekonwertować numeryczne, `Boolean`, lub wartość daty/godziny `String`. Można również przeprowadzić konwersję w odwrotnym kierunku — od wartości ciągu na liczbowe `Boolean`, lub `Date` — pod warunkiem zawartość ciągu mogą być interpretowane jako prawidłowa wartość docelowego typu danych. Jeśli nie jest to możliwe, wystąpi błąd czasu wykonywania.  
  
 Konwersje dla wszystkich tych przypisań w dowolnym kierunku to zawężających. Należy użyć słowa kluczowe konwersji typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, i `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A> i <xref:Microsoft.VisualBasic.Conversion.Val%2A> funkcje zapewniają dodatkową kontrolę nad Konwertowanie pomiędzy ciągami a liczb.  
  
 Jeśli zdefiniowano klasy lub struktury, można zdefiniować typ operatory konwersji między `String` i typ klasy lub struktury. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Konwersja liczb na ciągi  
 Możesz użyć `Format` funkcji w celu przekonwertowania liczby na sformatowany ciąg, który może zawierać nie tylko odpowiednie cyfr, ale również formatowanie symbole, takie jak podpisywanie waluty (takie jak `$`), tysięcy separatory lub *grupowania cyfr symbole* (takie jak `,`) i separator dziesiętny (takie jak `.`). `Format` automatycznie używa odpowiednich symboli, zgodnie z opisem w **Opcje regionalne** ustawień określonych w Windows **Panelu sterowania**.  
  
 Należy pamiętać, że łączenie (`&`) — operator może Konwertuj liczbę na ciąg niejawnie, co ilustruje poniższy przykład.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Konwersja ciągów na liczby  
 Możesz użyć `Val` funkcję, aby jawnie przekonwertować na liczbę cyfr w ciągu. `Val` odczytuje parametry, aż do napotkania znak inny niż znak cyfry, miejsca, karta, wysuw wiersza lub okres. Sekwencje "&" i "& H" alter podstawę systemu liczbowego i zakończenie skanowania. Do jej zamknięcia czytelności `Val` konwertuje wszystkie znaki odpowiednią wartość liczbową. Na przykład następująca instrukcja zwraca wartość `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Gdy Visual Basic konwertuje ciąg na wartość liczbową, używa **Opcje regionalne** ustawień określonych w Windows **Panelu sterowania** interpretowanie tysięcy separator, separator dziesiętny, i symbol waluty. Oznacza to, że konwersja może się powieść w jednej ustawienie, ale nie do innego. Na przykład `"$14.20"` jest dopuszczalna w ustawieniach regionalnych języka angielskiego (Stany Zjednoczone), ale nie w dowolnych francuska ustawień regionalnych.  
  
## <a name="see-also"></a>Zobacz także

- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
