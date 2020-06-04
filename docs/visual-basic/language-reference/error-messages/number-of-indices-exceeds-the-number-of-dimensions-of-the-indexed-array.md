---
title: Liczba indeksów przekracza liczbę wymiarów tablicy indeksowanej
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 4d8ffd2c4ad0a386053ced0f98503969723c7168
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409377"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>Liczba indeksów przekracza liczbę wymiarów tablicy indeksowanej
Liczba indeksów używanych w celu uzyskania dostępu do elementu tablicy musi być dokładnie taka sama jak ranga tablicy, czyli liczba dla nich wymiarów.  
  
 **Identyfikator błędu:** BC30106  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń indeksy dolne z odwołania do tablicy do momentu, aż całkowita liczba indeksów jest równa rangi tablicy. Przykład:  
  
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

- [Tablice](../../programming-guide/language-features/arrays/index.md)
