---
title: Granice tablicy nie mogą wystąpić w specyfikatorze typu
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512760"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Granice tablicy nie mogą wystąpić w specyfikatorze typu

Nie można zadeklarować rozmiarów tablicy jako części specyfikatora typu danych.

**Identyfikator błędu:** BC30638

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Określ rozmiar tablicy bezpośrednio po nazwie zmiennej zamiast umieszczania rozmiaru tablicy po typie, jak pokazano w poniższym przykładzie.

  ```vb
  Dim Array(8) As Integer
  ```

- Zdefiniuj tablicę i zainicjuj ją przy użyciu żądanej liczby elementów, jak pokazano w poniższym przykładzie.

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>Zobacz także

- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
