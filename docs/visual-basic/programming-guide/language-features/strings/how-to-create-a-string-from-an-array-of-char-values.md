---
title: 'Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)
W tym przykładzie tworzy ciągu "abcd" z poszczególnych znaków.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ta metoda nie ma specjalnych wymagań.  
  
 Składnia `"a"c`, w którym jeden `c` następuje jeden znak w znaki cudzysłowu, służy do tworzenia literału znaku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Znaki null (odpowiednikiem `Chr(0)`) w ciągu dać nieoczekiwane wyniki, korzystając z ciągu. Znak null zostanie uwzględniony w ciągu, ale nie będą wyświetlane po znaku null w niektórych sytuacjach.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String>  
 [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
