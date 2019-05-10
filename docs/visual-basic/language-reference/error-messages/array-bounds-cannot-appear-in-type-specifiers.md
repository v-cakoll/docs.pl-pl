---
title: Granice tablicy nie mogą wystąpić w specyfikatorze typu
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 50e1cd0e41da467a9e816c8e5d64d09a36923d65
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665749"
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
