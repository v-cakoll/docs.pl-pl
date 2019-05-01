---
title: 'Instrukcje: Tworzenie ciągu z tablicy wartości znaków (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 1f72cb86ffa38dc929062fab2f5592a781f2de27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054058"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Instrukcje: Tworzenie ciągu z tablicy wartości znaków (Visual Basic)
W tym przykładzie tworzy ciągu "abcd" na podstawie poszczególnych znaków.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ta metoda nie ma żadnych specjalnych wymagań.  
  
 Składnia `"a"c`, w którym jeden `c` następuje pojedynczy znak w cudzysłów, służy do tworzenia znak literału.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Znaki null (równoważne `Chr(0)`) w ciągu prowadzić do nieoczekiwanych wyników przy użyciu ciągu. Znak null, będzie ona uwzględniona w ciągu, ale znaki po znaku null nie będą wyświetlane w niektórych sytuacjach.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.String>
- [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
