---
title: 'Instrukcje: Konwertowanie ciągu na tablicę znaków w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: 921d7ad62545d3a29870aee6c6b354fdadeb0500
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823314"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Instrukcje: Konwertowanie ciągu na tablicę znaków w języku Visual Basic
Czasami przydatne jest zapewnienie dane dotyczące znaków w ciągu i położenie tych znaków w ciągu, na przykład gdy są analizowania parametrów. W tym przykładzie pokazano, jak uzyskać tablicę znaków w ciągu, wywołując ciągu <xref:System.String.ToCharArray%2A> metody.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i jak pozwala podzielić ciąg do `String` tablicy jej znaków Unicode, tekst. Przyczyna wykonywania tego rozróżnienia to, że znaki tekstowe Unicode mogą się składać z co najmniej dwóch `Char` znaki (np. para zastępcza lub łączenie sekwencji znaków). Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i [Unicode Standard](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Przykład  
 Jest trudniejsze do podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualnej reprezentacji ciągu. W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje, które tworzą ciąg znaków Unicode.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Instrukcje: Dostęp do znaków w ciągach](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
