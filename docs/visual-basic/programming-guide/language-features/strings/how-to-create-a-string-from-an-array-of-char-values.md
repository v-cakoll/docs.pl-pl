---
title: 'Porady: tworzenie ciągu z tablicy wartości znaków'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344386"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)
Ten przykład tworzy ciąg "abcd" z pojedynczych znaków.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ta metoda nie ma specjalnych wymagań.  
  
 Składnia `"a"c`, w której jeden `c` następuje po pojedynczym znaku w cudzysłowie, jest używany do tworzenia literału znakowego.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Znaki null (równoważne `Chr(0)`) w ciągu powodują nieoczekiwane wyniki przy użyciu ciągu. Znak null zostanie dołączony do ciągu, ale znaki po znaku null nie będą wyświetlane w niektórych sytuacjach.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.String>
- [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
