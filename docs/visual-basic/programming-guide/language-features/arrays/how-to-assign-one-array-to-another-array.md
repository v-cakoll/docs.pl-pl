---
title: 'Porady: przypisywanie tablicy do innej tablicy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647933"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Porady: przypisywanie tablicy do innej tablicy (Visual Basic)
Ponieważ tablic są obiektami, można używać ich w instrukcji przypisania, podobnie jak inne typy obiektów. Zmienną tablicową zawiera wskaźnik do stanowiące elementów tablicy i informacje o randze i długość danych, i przypisania kopiuje tylko ten wskaźnik.  
  
### <a name="to-assign-one-array-to-another-array"></a>Aby przypisywanie tablicy do innej tablicy  
  
1.  Upewnij się, że dwóch tablic mają taką samą rangę (liczba wymiarów) i element niezgodne typy danych.  
  
2.  Użyj instrukcji przypisania standardowych można przypisać tablicy źródłowej do tablicy docelowej. Nie wykonuj albo nazwa tablicy w nawiasach.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Po przypisaniu tablicy do innej, obowiązują następujące reguły:  
  
-   **Taki sam rangi.** (Liczba wymiarów) rangę tablicy docelowej musi być taka sama jak tablicy źródłowej.  
  
     Zakładając, że rangi dwóch tablic są takie same, wymiary nie są równe. Liczba elementów w określonym wymiarze można zmienić podczas przypisywania.  
  
-   **Typy elementów.** Musi mieć albo obu tablice *zawierają odwołania do typu* elementy lub obu tablic musi mieć *typu wartości* elementów. Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Jeśli oba tablice elementów typu wartości, typy elementów danych muszą być dokładnie takie same. Jedynym wyjątkiem jest przypisanie tablicę `Enum` elementów do tablicy typu podstawowego `Enum`.  
  
    -   Jeśli obydwie tablice elementów Typ odwołania, typu elementu źródłowego musi pochodzić od typu elementu docelowego. W przypadku dwóch tablic mieć tej samej relacji dziedziczenia jako ich elementów. Ta metoda jest wywoływana *Kowariancja tablicy*.  
  
 Kompilator zgłasza błąd, jeśli powyższe zasady naruszenia, na przykład jeśli typy danych są niezgodne lub rangę nie są równe. Możesz dodać obsługę błędów do swój kod, aby upewnić się, że tablice są zgodne, przed podjęciem próby wykonania przypisania. Można również użyć [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) — słowo kluczowe, jeśli chcesz uniknąć generowania wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
