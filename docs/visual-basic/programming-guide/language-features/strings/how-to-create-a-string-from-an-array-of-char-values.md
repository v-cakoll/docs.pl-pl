---
title: "Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [CHAR — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
