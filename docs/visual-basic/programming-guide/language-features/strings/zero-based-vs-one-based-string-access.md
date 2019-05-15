---
title: Dostęp do ciągu liczonego od zera a Dostęp do ciągu liczonego od jednego w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591751"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Dostęp do ciągu liczonego od zera a Dostęp do ciągu liczonego od jednego w języku Visual Basic
W tym temacie przedstawiono porównanie, w jaki Visual Basic i .NET Framework zapewnia dostęp do znaków w ciągu. .NET Framework zawsze udostępnia liczony od zera znaków w ciągu, natomiast języka Visual Basic udostępnia liczony od zera i jednobazowa, w zależności od funkcji.  
  
## <a name="one-based"></a>Liczonego od jednego  
 Na przykład funkcję liczonego od jednego języka Visual Basic należy wziąć pod uwagę `Mid` funkcji. Trwa argument, który wskazuje pozycję znaku, w którym podciąg rozpocznie się, zaczynając od pozycji 1. .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda przyjmuje indeks znaku w ciągu, w którym podciąg jest uruchomienie, zaczynając od pozycji 0. W związku z tym, jeśli ciąg "ABCDE", pojedyncze znaki są numerowane 1,2,3,4,5 do użytku z programem `Mid` funkcji, ale 0,1,2,3,4 do użytku z programem <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.  
  
## <a name="zero-based"></a>Liczony od zera  
 Na przykład liczony od zera funkcja języka Visual Basic należy wziąć pod uwagę `Split` funkcji. On dzieli ciąg i zwraca tablicę zawierającą podciągów. .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> metoda również dzieli ciąg i zwraca tablicę zawierającą podciągów. Ponieważ `Split` funkcji i <xref:System.String.Split%2A> metody zwracają tablice platformy .NET Framework, muszą one być liczony od zera.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
