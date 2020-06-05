---
title: Dostęp do ciągów opartych na protokole zero zamiast jednego
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: ce2fcb2610c09a9591a5fd79da4baa74cc533c99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363659"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Dostęp do ciągów opartych na zerze i na jedynce w Visual Basic
W tym temacie porównano, jak Visual Basic i .NET Framework zapewniają dostęp do znaków w ciągu. .NET Framework zawsze zapewnia od zera dostęp do znaków w ciągu, podczas gdy Visual Basic zapewnia dostęp oparty na zerowym i jednokrotnym, w zależności od funkcji.  
  
## <a name="one-based"></a>Oparte na jednym  
 Przykład funkcji Visual Basic opartej na jednym miejscu, należy wziąć pod uwagę `Mid` funkcję. Przyjmuje argument, który wskazuje położenie znaku, w którym rozpocznie się podciąg, zaczynając od pozycji 1. Metoda .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> przyjmuje indeks znaku w ciągu, w którym ma zostać uruchomiony podciąg, zaczynając od pozycji 0. W takim przypadku, jeśli masz ciąg "ABCDe", poszczególne znaki są numerowane 1, 2, 3, 4, 5 do użycia z `Mid` funkcją, ale 0, 1, 2, 3, 4 do użycia z <xref:System.String.Substring%2A?displayProperty=nameWithType> metodą.  
  
## <a name="zero-based"></a>W oparciu o zero  
 Przykład funkcji Visual Basic opartej na zero, należy wziąć pod uwagę `Split` funkcję. Dzieli ciąg i zwraca tablicę zawierającą podciągi. Metoda .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> dzieli również ciąg i zwraca tablicę zawierającą podciągi. Ponieważ `Split` Funkcja i <xref:System.String.Split%2A> metoda zwracają .NET Framework tablic, muszą one być oparte na zero.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Wprowadzenie do ciągów w Visual Basic](introduction-to-strings.md)
