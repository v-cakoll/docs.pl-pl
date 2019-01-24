---
title: 'Instrukcje: Tworzenie ciągu z tablicy wartości znaków (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: a067474d6b32589a34b031d5c3ea4e5a4be55834
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611465"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Instrukcje: Tworzenie ciągu z tablicy wartości znaków (Visual Basic)
W tym przykładzie tworzy ciągu "abcd" na podstawie poszczególnych znaków.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ta metoda nie ma żadnych specjalnych wymagań.  
  
 Składnia `"a"c`, w którym jeden `c` następuje pojedynczy znak w cudzysłów, służy do tworzenia znak literału.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Znaki null (równoważne `Chr(0)`) w ciągu prowadzić do nieoczekiwanych wyników przy użyciu ciągu. Znak null, będzie ona uwzględniona w ciągu, ale znaki po znaku null nie będą wyświetlane w niektórych sytuacjach.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.String>
- [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
