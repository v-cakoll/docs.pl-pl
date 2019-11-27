---
title: Dostęp do ciągów opartych na protokole zero zamiast jednego
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354297"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Dostęp do ciągów opartych na zerze i na jedynce w Visual Basic
W tym temacie porównano, jak Visual Basic i .NET Framework zapewniają dostęp do znaków w ciągu. .NET Framework zawsze zapewnia od zera dostęp do znaków w ciągu, podczas gdy Visual Basic zapewnia dostęp oparty na zerowym i jednokrotnym, w zależności od funkcji.  
  
## <a name="one-based"></a>Oparte na jednym  
 Aby zapoznać się z przykładem funkcji Visual Basic opartej na jednym z nich, należy wziąć pod uwagę funkcję `Mid`. Przyjmuje argument, który wskazuje położenie znaku, w którym rozpocznie się podciąg, zaczynając od pozycji 1. Metoda .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> przyjmuje indeks znaku w ciągu, w którym ma zostać uruchomiony podciąg, zaczynając od pozycji 0. W takim przypadku, jeśli masz ciąg "ABCDe", poszczególne znaki są numerowane 1, 2, 3, 4, 5, do użytku z funkcją `Mid`, ale 0, 1, 2, 3, 4 do użycia z metodą <xref:System.String.Substring%2A?displayProperty=nameWithType>.  
  
## <a name="zero-based"></a>W oparciu o zero  
 Przykład funkcji Visual Basic opartej na zero, należy wziąć pod uwagę funkcję `Split`. Dzieli ciąg i zwraca tablicę zawierającą podciągi. Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> .NET Framework dzieli również ciąg i zwraca tablicę zawierającą podciągi. Ponieważ funkcja `Split` i Metoda <xref:System.String.Split%2A> zwracają .NET Framework tablice, muszą one być oparte na zero.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
