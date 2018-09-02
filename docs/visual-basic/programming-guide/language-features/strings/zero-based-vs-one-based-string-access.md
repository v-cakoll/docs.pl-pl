---
title: Liczony od zera programu vs. Dostęp do ciągu liczonego od jednego w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a0a42f72d94adf1c10865374017fa61e833df40f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461673"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Liczony od zera programu vs. Dostęp do ciągu liczonego od jednego w języku Visual Basic
W tym temacie porównano jak Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zapewniają dostęp do znaków w ciągu. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Zawsze udostępnia liczony od zera dla znaków w ciągu, Visual Basic przewiduje liczony od zera i oparte na jednym dostępu, w zależności od funkcji.  
  
## <a name="one-based"></a>Liczonego od jednego  
 Na przykład funkcję liczonego od jednego języka Visual Basic należy wziąć pod uwagę `Mid` funkcji. Trwa argument, który wskazuje pozycję znaku, w którym podciąg rozpocznie się, zaczynając od pozycji 1. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda przyjmuje indeks znaku w ciągu, w którym podciąg jest uruchomienie, zaczynając od pozycji 0. W związku z tym, jeśli ciąg "ABCDE", pojedyncze znaki są numerowane 1,2,3,4,5 do użytku z programem `Mid` funkcji, ale 0,1,2,3,4 do użytku z programem <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.  
  
## <a name="zero-based"></a>Liczony od zera  
 Na przykład liczony od zera funkcja języka Visual Basic należy wziąć pod uwagę `Split` funkcji. On dzieli ciąg i zwraca tablicę zawierającą podciągów. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda również dzieli ciąg i zwraca tablicę zawierającą podciągów. Ponieważ `Split` funkcji i <xref:System.String.Split%2A> zwrotu metody [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tablic, muszą one być liczony od zera.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
