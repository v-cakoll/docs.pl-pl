---
title: 'Porady: tworzenie ciągu z tablicy wartości znaków'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: d9ec897467f0caac0afc089a028516c0316a2bda
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410596"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)
Ten przykład tworzy ciąg "abcd" z pojedynczych znaków.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Ta metoda nie ma specjalnych wymagań.  
  
 Składnia `"a"c` , w której pojedynczy `c` znak w cudzysłowie jest używany do tworzenia literału znakowego.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Znaki null (równoważne `Chr(0)` ) w ciągu powodują nieoczekiwane wyniki przy użyciu ciągu. Znak null zostanie dołączony do ciągu, ale znaki po znaku null nie będą wyświetlane w niektórych sytuacjach.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.String>
- [Char, typ danych](../../../language-reference/data-types/char-data-type.md)
- [Typy danych](../data-types/index.md)
