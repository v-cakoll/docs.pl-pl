---
title: Char — Typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: b50c902f69f7602dbad4663dc35bf0a2b932973f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796984"
---
# <a name="char-data-type-visual-basic"></a>Char — Typ danych (Visual Basic)
Wskazuje niepodpisanego kodu (2-bajtowych) 16-bitowych blokady z zakresu od 0 do 65 535. Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Char` — typ danych Jeśli potrzebujesz do przechowywania tylko jeden znak i nie trzeba korzystać z `String`. W niektórych przypadkach można użyć `Char()`, tablicę `Char` elementy do przechowywania wielu znaków.  
  
 Wartość domyślna `Char` to znak z punktem kodu w 0.  
  
## <a name="unicode-characters"></a>Znaki Unicode  
 Pierwsze punkty kodowe 128 (0 – 127), znaków Unicode odpowiadają litery i symbole na klawiaturze standardowej Stanów Zjednoczonych. Te pierwsze punkty kodowe 128 są takie same, jak definiuje zestaw znaków ASCII. Drugi 128 punkty kodowe (128-255) reprezentują znaków specjalnych, takich jak litery alfabetu alfabetu łacińskiego, akcentów, symbole walut i ułamki. Unicode używa pozostałe punkty kodowe (256-65535) dla szerokiej gamy symbole, w tym znaki tekstowe na całym świecie, znaki diakrytyczne i symbole matematyczne i technicznych.  
  
 Można użyć metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na `Char` zmiennej, aby określić klasyfikację Unicode.  
  
## <a name="type-conversions"></a>Konwersje typu  
 Visual Basic nie konwertuje bezpośrednio między `Char` typy liczbowe. Możesz użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkcję, aby skonwertować `Char` wartość `Integer` reprezentujący jego punkt kodu. Możesz użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkcję, aby skonwertować `Integer` wartość `Char` zawierający ten punkt kodu.  
  
 Jeśli kontrola typów w przełącznik ([Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literalny typu do jednoznakowy ciąg literału w celu zidentyfikowania go jako `Char` typu danych. Ilustruje to poniższy przykład.  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Liczby ujemne.** `Char` jest typ bez znaku, a nie może reprezentować wartość ujemną. W każdym przypadku, nie należy używać `Char` do przechowywania wartości liczbowych.  
  
- **Uwagi dotyczące współdziałania.** Jeśli interfejs ze składnikami programu .NET Framework na przykład obiektami automatyzacji lub COM, pamiętaj, że znaki — typy mają różną szerokość danych (8 bitów) w innych środowiskach. Jeśli przekażesz 8-bitowy argument do takiego składnika, Zadeklaruj go jako `Byte` zamiast `Char` nowego kodu języka Visual Basic.  
  
- **Rozszerzanie.** `Char` — Typ danych rozszerza się na `String`. Oznacza to, że możesz przekonwertować `Char` do `String` i nie będzie występować <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaku typu literał `C` na ciąg pojedynczych znaków literału wymusza `Char` typu danych. `Char` nie ma identyfikatora typ znaku.  
  
- **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Char?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
