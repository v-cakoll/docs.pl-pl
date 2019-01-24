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
ms.openlocfilehash: 9d68e3d90c52d6a4312ccb7c0c9610968e7a4b55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603758"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Instrukcje: Konwertowanie ciągu na tablicę znaków w języku Visual Basic
Czasami przydatne jest zapewnienie dane dotyczące znaków w ciągu i położenie tych znaków w ciągu, na przykład gdy są analizowania parametrów. W tym przykładzie pokazano, jak uzyskać tablicę znaków w ciągu, wywołując ciągu <xref:System.String.ToCharArray%2A> metody.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i jak pozwala podzielić ciąg do `String` tablicy jej znaków Unicode, tekst. Przyczyna wykonywania tego rozróżnienia to, że znaki tekstowe Unicode mogą się składać z co najmniej dwóch `Char` znaki (np. para zastępcza lub łączenie sekwencji znaków). Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i [Unicode Standard](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Przykład  
 Jest trudniejsze do podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualnej reprezentacji ciągu. W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje, które tworzą ciąg znaków Unicode.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Instrukcje: Dostęp do znaków w ciągach](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
