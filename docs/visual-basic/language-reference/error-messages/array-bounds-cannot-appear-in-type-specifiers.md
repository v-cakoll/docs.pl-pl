---
title: Granice tablicy nie mogą wystąpić w specyfikatorze typu
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 45787db51de562f2266c587fd2bb15ef29ebefbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Granice tablicy nie mogą wystąpić w specyfikatorze typu
Rozmiar tablicy nie można zadeklarować jako część specyfikatora typu danych.  
  
 **Identyfikator błędu:** BC30638  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ rozmiar tablicy, natychmiast po nazwę zmiennej, zamiast wprowadzania do rozmiaru tablicy po typie, jak pokazano w poniższym przykładzie.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Zdefiniuj tablicy i zainicjować go z odpowiednią liczbę elementów, jak pokazano w poniższym przykładzie.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
