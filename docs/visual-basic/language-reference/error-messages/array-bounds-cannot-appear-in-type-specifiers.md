---
title: Granice tablicy nie mogą wystąpić w specyfikatorze typu
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f31aea5a98233c8f262a77ba5c99eea389bc33ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715442"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Granice tablicy nie mogą wystąpić w specyfikatorze typu
Rozmiar tablicy nie można zadeklarować jako część specyfikatora typu danych.  
  
 **Identyfikator błędu:** BC30638  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ rozmiar tablicy, natychmiast po nazwę zmiennej, zamiast wykonywać rozmiaru tablicy po typie, jak pokazano w poniższym przykładzie.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Zdefiniować tablicę i zainicjuj ją z odpowiednią liczbę elementów, jak pokazano w poniższym przykładzie.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
