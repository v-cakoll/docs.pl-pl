---
title: "Porady: konwertowanie ciągów w tablice bajtów w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6d527434dc0a61c9c771b42d05c1ee316094e7fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Porady: konwertowanie ciągów w tablice bajtów w Visual Basic
W tym temacie pokazano, jak przekonwertować ciąg na tablicę bajtów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Text.Encoding.GetBytes%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasę, aby przekonwertować ciąg na tablicę bajtów.  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 Możesz wybrać kilka opcji kodowania, aby przekonwertować ciąg na tablicę bajtów:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera kodowanie znaków ASCII (7-bitowym) Ustaw.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowanie formatu UTF-16, używając kolejności bajtów big endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowanie formatu UTF-16, używając kolejności bajtów little endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowanie przy użyciu kolejności bajtów little endian formatu UTF-32.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowania w formacie UTF-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowania w formacie UTF-8.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [Porady: Konwertowanie tablicy bajtów w ciąg w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
