---
title: Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbc418147a83b93f94449beb607d7f6bc3eff7a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic
W tym temacie porównuje jak Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zapewniają dostęp do znaków w ciągu. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Zawsze zapewnia liczony od zera dostęp do znaków w ciągu, Visual Basic stanowi liczony od zera i jedynki dostęp, w zależności od funkcji.  
  
## <a name="one-based"></a>Na podstawie jednej  
 Na przykład funkcję języka Visual Basic na podstawie co należy wziąć pod uwagę `Mid` funkcji. Trwa argument, który wskazuje pozycję znaków, jaką rozpocznie podciąg, zaczynając od pozycji 1. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda przyjmuje indeksu znaku w ciągu, w którym ma rozpocząć, podciąg zaczynając od pozycji 0. W związku z tym, jeśli masz ciąg "ABCDE" poszczególnych znaków są numerowane 1,2,3,4,5 do użytku z `Mid` funkcji, ale 0,1,2,3,4 do użytku z <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.  
  
## <a name="zero-based"></a>Liczony od zera  
 Na przykład liczony od zera funkcja języka Visual Basic, należy wziąć pod uwagę `Split` funkcji. Dzieli się ciągiem, a zwraca tablicę zawierającą podciągów. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda również dzieli się ciągiem i zwraca tablicę zawierającą podciągów. Ponieważ `Split` funkcji i <xref:System.String.Split%2A> metody zwracany [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tablic, muszą być liczony od zera.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
