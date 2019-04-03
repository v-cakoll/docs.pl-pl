---
title: Oczekiwano końca instrukcji
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: ab6a4a0e6736e2af9c1fa0dd170b6aa4c42d9e4a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817157"
---
# <a name="end-of-statement-expected"></a>Oczekiwano końca instrukcji
Instrukcja jest syntaktycznie ukończone, ale dodatkowy element programowania następuje po elemencie, kończące instrukcję. Terminator wiersza jest wymagany na końcu każdej instrukcji.
  
 Terminator wiersza dzieli znaki plik źródłowy w języku Visual Basic na wierszach. Terminatory wiersza przykłady Unicode karetki zwracany znak (& HD), Unicode wysuwu wiersza znaku (i wysokiej dostępności) i następuje znak wysuwu wiersza Unicode znak powrotu karetki Unicode. Aby uzyskać więcej informacji na temat terminatory wiersza zobacz [specyfikacja języka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **Identyfikator błędu:** BC30205
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
  
1.  Sprawdź, jeśli dwie różne instrukcje zostały przypadkowo wprowadzone w tym samym wierszu.
  
2.  Wstaw terminator wiersza po elemencie, kończące instrukcję.
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
