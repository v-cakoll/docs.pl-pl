---
title: 'Instrukcje: wyszukiwanie w ciągu Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700059"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Instrukcje: wyszukiwanie w ciągu (Visual Basic)

W tym artykule przedstawiono przykład sposobu wyszukiwania ciągu w Visual Basic.

## <a name="example"></a>Przykład

Ten przykład wywołuje metodę <xref:System.String.IndexOf%2A> w obiekcie <xref:System.String>, aby zgłosić indeks pierwszego wystąpienia podciągu:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Niezawodne programowanie

Metoda <xref:System.String.IndexOf%2A> zwraca lokalizację pierwszego znaku pierwszego wystąpienia podciągu. Indeks jest oparty na 0, co oznacza, że pierwszy znak ciągu ma indeks 0.

Jeśli <xref:System.String.IndexOf%2A> nie odnajdzie podciągu, zwraca-1.

W metodzie <xref:System.String.IndexOf%2A> jest rozróżniana wielkość liter i jest stosowana bieżąca kultura.

Aby zapewnić optymalną kontrolę błędów, możesz chcieć ująć ciąg wyszukiwania w bloku `Try` [try... Catch... Konstrukcja instrukcji finally](../../../language-reference/statements/try-catch-finally-statement.md) .

## <a name="see-also"></a>Zobacz także

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally, instrukcja](../../../language-reference/statements/try-catch-finally-statement.md)
- [Wprowadzenie do ciągów w Visual Basic](introduction-to-strings.md)
- [Ciągi](index.md)
