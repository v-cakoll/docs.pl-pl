---
title: 'Porady: konwertowanie ciągu do tablicy znaków'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: eca8cd7be8da1f6149dadf1e9edeab5e5225ab9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360673"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Porady: konwertowanie ciągu do tablicy znaków w Visual Basic
Czasami warto mieć dane dotyczące znaków w ciągu i położenia tych znaków w ciągu, np. podczas analizowania ciągu. Ten przykład pokazuje, jak można uzyskać tablicę znaków w ciągu, wywołując <xref:System.String.ToCharArray%2A> metodę ciągu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak podzielić ciąg na `Char` tablicę i jak podzielić ciąg na `String` tablicę znaków tekstu Unicode. Przyczyną tego rozróżnienia jest to, że znaki tekstowe Unicode mogą składać się z co najmniej dwóch `Char` znaków (takich jak para zastępcza lub sekwencja znaków łączących). Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i [standard Unicode](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Przykład  
 Trudno jest podzielić ciąg na znaki tekstowe Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualnej reprezentacji ciągu. W tym przykładzie używa <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metody, aby uzyskać informacje o znakach tekstowych Unicode, które tworzą ciąg.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Porady: dostęp do znaków w ciągach](how-to-access-characters-in-strings.md)
- [Konwertowanie pomiędzy ciągami a innymi typami danych w Visual Basic](converting-between-strings-and-other-data-types.md)
- [Ciągi](index.md)
