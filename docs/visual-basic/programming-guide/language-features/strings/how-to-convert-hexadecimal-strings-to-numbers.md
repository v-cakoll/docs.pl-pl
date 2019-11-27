---
title: 'Porady: konwertowanie ciągów szestnastkowych na numery'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347173"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Porady: konwertowanie ciągów szestnastkowych na numery (Visual Basic)

Ten przykład konwertuje ciąg szesnastkowy na liczbę całkowitą przy użyciu metody <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Aby skonwertować ciąg szesnastkowy na liczbę

- Użyj metody <xref:System.Convert.ToInt32(System.String,System.Int32)>, aby skonwertować liczbę wyrażoną w podstawie od 16 do liczbę całkowitą.

  Pierwszym argumentem metody <xref:System.Convert.ToInt32(System.String,System.Int32)> jest ciąg do przekonwertowania. Drugi argument określa podstawę, w której jest wyrażona liczba; szesnastkowa to 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Należy pamiętać, że ciąg szesnastkowy ma następujące ograniczenia:

  - Nie może zawierać prefiksu `&h`.
  - Nie może zawierać separatora cyfr `_`.

  Jeśli jest obecny prefiks lub separator cyfr, wywołanie metody <xref:System.Convert.ToInt32(System.String,System.Int32)> zgłasza <xref:System.FormatException>.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
