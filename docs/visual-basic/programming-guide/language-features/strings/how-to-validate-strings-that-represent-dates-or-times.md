---
title: 'Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5d153ac29039375386b3cd5f03609b1e4bd1d5bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410570"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)
Poniższy przykład kodu ustawia `Boolean` wartość wskazującą, czy ciąg reprezentuje prawidłową datę lub godzinę.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Zamień `("01/01/03")` i `"9:30 PM"` datę i godzinę, którą chcesz zweryfikować. Można zastąpić ciąg innym zakodowanym ciągiem, ze `String` zmienną lub metodą zwracającą ciąg, na przykład `InputBox` .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Użyj tej metody, aby sprawdzić poprawność ciągu przed próbą przekonwertowania `String` na `DateTime` zmienną. Sprawdzając najpierw datę lub godzinę, można uniknąć generowania wyjątku w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](validating-strings.md)
