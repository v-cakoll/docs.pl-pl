---
title: Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a0a42f72d94adf1c10865374017fa61e833df40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649103"
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
