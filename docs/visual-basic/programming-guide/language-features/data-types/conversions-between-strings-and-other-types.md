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
ms.openlocfilehash: 40a28d664bc6ed3d094ccc7c342d6411fe88fd7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650572"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)
Możesz przekształcić liczbową, `Boolean`, lub wartości daty/godziny `String`. Można również przeprowadzić konwersję w kierunku odwrotnym — z wartości ciągu na liczbowe, `Boolean`, lub `Date` — pod warunkiem zawartość ciąg może zostać zinterpretowany jako prawidłowa wartość docelowego typu danych. Jeśli nie, występuje błąd w czasie wykonywania.  
  
 Konwersje wszystkich tych przydziałów w żadnym kierunku są zawężanie konwersji. Należy używać słowa kluczowe konwersji typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, i `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A> i <xref:Microsoft.VisualBasic.Conversion.Val%2A> funkcje zapewniają dodatkową kontrolę nad Konwertowanie pomiędzy ciągami a cyfry.  
  
 Jeśli zdefiniowano klasę lub strukturę można zdefiniować typu operatory konwersji między `String` i typu klasy lub struktury. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Konwersja liczb znajdujących się na ciągi  
 Można użyć `Format` funkcja Konwertuj liczbę na ciąg formatowania, może zawierać nie tylko odpowiednie cyfr, ale również formatowanie symbole, takie jak znak waluty (takich jak `$`), tysięcy separatorów lub *grupowania cyfr symbole* (takich jak `,`) i separator dziesiętny (takie jak `.`). `Format` automatycznie wykorzystuje odpowiednie symbole zgodnie z **Opcje regionalne** ustawienia określone w oknach **Panelu sterowania**.  
  
 Należy pamiętać, że połączenie (`&`) — operator może konwertowanie liczby na ciąg niejawnie w poniższym przykładzie pokazano.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Konwersja ciągów na liczby  
 Można użyć `Val` funkcji, aby jawnie przekonwertować na liczbę cyfr w ciągu. `Val` odczytuje ciąg, aż do napotkania znaków innych niż cyfry, miejsca, karta, wysuwu wiersza lub okres. Sekwencje "&" i "& H" alter podstawą układzie i zakończenie skanowania. Do jej zamknięcia czytania, `Val` konwertuje wszystkie znaki odpowiednią wartość liczbowa. Na przykład następująca instrukcja zwraca wartość `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Gdy Visual Basic konwertuje ciąg na wartość numeryczną, używa **Opcje regionalne** ustawienia określone w oknach **Panelu sterowania** interpretować tysięcy separator, separator dziesiętny, i symbol waluty. Oznacza to, że konwersja może się powieść w jednej ustawienie, ale nie inna. Na przykład `"$14.20"` jest akceptowalne z ustawieniami regionalnymi Angielski (Stany Zjednoczone), ale nie w dowolnych francuskim ustawień regionalnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Porady: konwertowanie obiektu do innego typu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
