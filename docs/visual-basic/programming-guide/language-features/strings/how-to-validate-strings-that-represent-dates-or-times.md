---
title: 'Instrukcje: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 1a838d9d156ad9c05a70a4d4d72db1a288731c9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685402"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Instrukcje: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)
Poniższy kod ustawia przykład `Boolean` wartość, która wskazuje, czy ciąg reprezentuje prawidłowej daty i godziny.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Zastąp `("01/01/03")` i `"9:30 PM"` z daty i godziny, którą chcesz zweryfikować. Można zastąpić ciąg z innego ciągu ustalonych `String` zmiennej, lub z metodą, zwraca wartość typu ciąg, takie jak `InputBox`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ta metoda służy do sprawdzenia ciągu przed próby skonwertowania `String` do `DateTime` zmiennej. Najpierw Sprawdzanie daty lub godziny, można uniknąć generowania wyjątku w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
