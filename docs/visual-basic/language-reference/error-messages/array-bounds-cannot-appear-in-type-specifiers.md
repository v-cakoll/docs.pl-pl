---
title: Granice tablicy nie mogą wystąpić w specyfikatorze typu
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935359"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Granice tablicy nie mogą wystąpić w specyfikatorze typu
Rozmiar tablicy nie można zadeklarować jako część specyfikatora typu danych.  
  
 **Identyfikator błędu:** BC30638  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Określ rozmiar tablicy, natychmiast po nazwę zmiennej, zamiast wykonywać rozmiaru tablicy po typie, jak pokazano w poniższym przykładzie.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
- Zdefiniować tablicę i zainicjuj ją z odpowiednią liczbę elementów, jak pokazano w poniższym przykładzie.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
