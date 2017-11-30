---
title: "Porady: wyszukiwanie wewnątrz ciągu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Porady: wyszukiwanie wewnątrz ciągu (Visual Basic)
W tym przykładzie wywołuje <xref:System.String.IndexOf%2A> metoda <xref:System.String> obiektu do zgłaszania indeks pierwszego wystąpienia podciągu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   `Imports` Określenie instrukcji <xref:System> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.String.IndexOf%2A> Metoda zgłasza lokalizacji pierwszego znaku pierwszego wystąpienia podciąg. Indeks jest oparty na 0, co oznacza, że pierwszy znak w ciągu ma indeks 0.  
  
 Jeśli <xref:System.String.IndexOf%2A> nie zwraca podciąg, zwraca -1.  
  
 <xref:System.String.IndexOf%2A> Metoda jest rozróżniana wielkość liter i używa bieżącej kultury.  
  
 Kontrolki optymalne błąd, możesz chcieć ujmij wyszukaj ciąg w `Try` zablokować z [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String.IndexOf%2A>  
 [Try... CATCH... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
