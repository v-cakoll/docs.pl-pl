---
title: 'Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348413"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)
Poniższy przykład kodu ustawia wartość `Boolean`, która wskazuje, czy ciąg reprezentuje prawidłową datę lub godzinę.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Zastąp `("01/01/03")` i `"9:30 PM"` datą i godziną, którą chcesz zweryfikować. Można zastąpić ciąg innym zakodowanym ciągiem zawierającym zmienną `String` lub metodę zwracającą ciąg, na przykład `InputBox`.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Użyj tej metody, aby sprawdzić poprawność ciągu przed próbą przekonwertowania `String` na zmienną `DateTime`. Sprawdzając najpierw datę lub godzinę, można uniknąć generowania wyjątku w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
