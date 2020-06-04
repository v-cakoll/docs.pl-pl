---
title: Oczekiwano końca instrukcji
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 169f01b02df377ba6cc21ffad53c36f5d4537140
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409650"
---
# <a name="end-of-statement-expected"></a>Oczekiwano końca instrukcji
Instrukcja ma składnię kompletną, ale dodatkowy element programistyczny następuje po elemencie, który uzupełnia instrukcję. Terminator wiersza jest wymagany na końcu każdej instrukcji.
  
 Terminator wiersza dzieli znaki pliku źródłowego Visual Basic na wiersze. Przykłady terminatorów wiersza to znak powrotu karetki Unicode (&HD), znak wysuwu wiersza Unicode (&HA) i znak powrotu karetki Unicode, po którym następuje znak wysuwu wiersza w formacie Unicode. Aby uzyskać więcej informacji na temat terminatorów wierszy, zobacz [Specyfikacja języka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **Identyfikator błędu:** BC30205
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
  
1. Sprawdź, czy dwie różne instrukcje zostały przypadkowo umieszczone w tym samym wierszu.
  
2. Wstaw terminator wiersza po elemencie, który uzupełnia instrukcję.
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: Przerywanie i łączenie instrukcji w kodzie](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
