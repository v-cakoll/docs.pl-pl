---
title: "Porady: konwertowanie ciągu do tablicy znaków w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59d0da52c8f78b93c76325e6242156c106deeaf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Porady: konwertowanie ciągu do tablicy znaków w Visual Basic
Czasami jest przydatne do danych o znaki w ciągu i pozycje te znaki w ciągu, na przykład gdy są analizowania parametrów. W tym przykładzie pokazano, jak wprowadzasz tablicy znaków w ciągu wywołując ciąg <xref:System.String.ToCharArray%2A> metody.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i dzielenia ciąg do `String` tablicy jego znaków Unicode. Przyczyna tej różnicy to, że znaków Unicode może składać się z co najmniej dwóch `Char` znaków (np. para zastępcza lub łączenie sekwencja znaków). Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i "Unicode Standard" w http://www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Przykład  
 Trudniej podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualną reprezentację ciągu. W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje na temat wchodzące w skład ciąg znaków Unicode.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Porady: dostęp do znaków w ciągach](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
