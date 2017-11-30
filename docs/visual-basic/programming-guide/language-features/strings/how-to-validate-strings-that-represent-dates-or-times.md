---
title: "Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)
Poniższy kod przykładzie `Boolean` wartość, która wskazuje, czy ciąg reprezentuje prawidłowej daty i godziny.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Zastąp `("01/01/03")` i `"9:30 PM"` Data i godzina, o których chcesz zweryfikować. Można zastąpić ciąg z innego ciągu ustalony `String` zmiennej, lub za pomocą metody która zwraca wartość typu ciąg, takie jak `InputBox`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ta metoda służy do sprawdzenia ciągu przed próby konwersji `String` do `DateTime` zmiennej. Najpierw Sprawdzanie daty lub godziny, można uniknąć generowania wyjątku w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
