---
title: "Granice tablicy nie mogą wystąpić w specyfikatorze typu"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
