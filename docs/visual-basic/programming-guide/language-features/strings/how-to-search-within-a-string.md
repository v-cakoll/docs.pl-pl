---
title: 'Instrukcje: Wyszukiwanie wewnątrz ciągu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 6ac75c99270deb14e23691d32e8ebf4e8b0a91b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542553"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Instrukcje: Wyszukiwanie wewnątrz ciągu (Visual Basic)
Ten przykład wywołuje <xref:System.String.IndexOf%2A> metody <xref:System.String> obiektu, aby zgłosić indeks pierwszego wystąpienia podciągu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   `Imports` Instrukcję, określając <xref:System> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.String.IndexOf%2A> Metoda zgłasza położenie pierwszego wystąpienia znaku pierwszego wystąpienia podciągu. Indeks jest oparty na 0, co oznacza, że pierwszym znakiem ciągu ma indeks 0.  
  
 Jeśli <xref:System.String.IndexOf%2A> nie zwraca podciąg, zwraca -1.  
  
 <xref:System.String.IndexOf%2A> Metoda jest uwzględniana wielkość liter i używa bieżącej kultury.  
  
 Dla formantu optymalne błąd, możesz chcieć ująć wyszukiwania ciągów w `Try` bloku [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukcji.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally, instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
