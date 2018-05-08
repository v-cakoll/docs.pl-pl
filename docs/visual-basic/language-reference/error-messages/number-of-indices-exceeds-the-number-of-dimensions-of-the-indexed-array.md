---
title: Liczba indeksów przekracza liczbę wymiarów tablicy indeksowanej
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: d40a19aefdca65773d3d8e37a43d99178586fb1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>Liczba indeksów przekracza liczbę wymiarów tablicy indeksowanej
Liczba indeksów, które umożliwiają dostęp do elementu tablicy muszą być dokładnie takie same rangą tablicy, czyli liczby wymiarów zadeklarowany dla niego.  
  
 **Identyfikator błędu:** BC30106  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń indeksy dolne z odwołaniem do tablicy, dopóki liczba indeksów dolnych equals rangą tablicy. Na przykład:  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
