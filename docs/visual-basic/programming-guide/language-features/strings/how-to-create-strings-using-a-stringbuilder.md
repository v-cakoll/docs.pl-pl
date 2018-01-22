---
title: "Porady: tworzenie ciągów za pomocą StringBuilder w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9def5da754d9075a8b498ac80e624caae5c97b96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Porady: tworzenie ciągów za pomocą StringBuilder w Visual Basic
Ten przykład tworzy ciąg z dużo mniejszym ciągów za pomocą <xref:System.Text.StringBuilder> klasy. <xref:System.Text.StringBuilder> Klasy jest bardziej efektywne niż `&=` operator łączenie wielu ciągów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągi do tego wystąpienia, a następnie zwraca reprezentacji ciągu.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)  
 [&=, operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)  
 [Manipulowanie ciągami](../../../../standard/base-types/manipulating-strings.md)  
 [Przykładowe ciągów](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)
