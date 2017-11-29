---
title: "Char — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16ff547fccbf4481d31ca79537962cc7090fc9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="char-data-type-visual-basic"></a>Char — Typ danych (Visual Basic)
Punkty niepodpisanego kodu (2-bajtowych) 16-bitowych blokady z zakresu od 0 do 65 535. Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Char` typu danych, gdy potrzebne do przechowywania tylko jeden znak i nie trzeba korzystać z `String`. W niektórych przypadkach można użyć `Char()`, tablicę `Char` elementów, aby pomieścić wielu znaków.  
  
 Wartość domyślna `Char` to znak o punkt kodu 0.  
  
## <a name="unicode-characters"></a>Znaki Unicode  
 Pierwszy punktów 128 kodu (0 – 127), znaków Unicode odpowiadają liter i symboli na klawiaturze standardowej Stanów Zjednoczonych. Pierwszy punkty 128 kodu są takie same jak definiuje zestaw znaków ASCII. Drugi punkty 128 kodu (128 – 255) reprezentują znaków specjalnych, takich jak litery alfabetu łacińskiego —, akcentów symbol waluty i ułamków. Unicode używa pozostałe punkty kodu (256-65535) dla różnych typów symboli, w tym na całym świecie tekstową znaków, znaków diakrytycznych i symbole matematyczne i technicznych.  
  
 Można użyć metody, takie jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na `Char` zmiennej do określenia jego klasyfikację Unicode.  
  
## <a name="type-conversions"></a>Konwersje typu  
 Visual Basic nie konwertuje bezpośrednio między `Char` typy liczbowe. Można użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkcji konwersji `Char` do wartości `Integer` reprezentujący punktu kodu. Można użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkcji konwersji `Integer` do wartości `Char` mający tego punktu kodu.  
  
 Jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literalny typu do jednoznakowym literału ciągu na identyfikację jako `Char` — typ danych. Ilustruje to poniższy przykład.  
  
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
  
-   **Wartości ujemne.** `Char`jest to typ bez znaku i nie może reprezentować wartość ujemną. W żadnym przypadku nie należy używać `Char` do przechowywania wartości liczbowych.  
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli interfejs ze składnikami, które nie są zapisywane dla programu .NET Framework dla obiektów automatyzacji lub COM przykład pamiętać, że znaki — typy są różne dane szerokości (8 bitów) w innych środowiskach. Argument 8-bitową w przypadku przekazania do tych składników, Zadeklaruj ją jako `Byte` zamiast `Char` w nowy kod Visual Basic.  
  
-   **Rozszerzanie.** `Char` Rozszerzenie typu danych do `String`. Oznacza to, że można przekonwertować `Char` do `String` i nie wystąpi <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znak literalny typu dołączanie `C` z ciągiem jednoznakowym literał wymusza `Char` — typ danych. `Char`nie ma identyfikatora typu znaku.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Char?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [String — typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
