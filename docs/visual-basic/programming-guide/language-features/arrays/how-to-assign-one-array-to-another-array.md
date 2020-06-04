---
title: 'Porady: przypisywanie tablicy do innej tablicy'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413082"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Porady: przypisywanie tablicy do innej tablicy (Visual Basic)

Ponieważ tablice są obiektami, można ich używać w instrukcjach przypisania, takich jak inne typy obiektów. Zmienna tablicowa zawiera wskaźnik do danych tworzących elementy tablicy oraz informacje o rangi i długości, a przypisanie kopiuje tylko ten wskaźnik.

### <a name="to-assign-one-array-to-another-array"></a>Aby przypisać jedną tablicę do innej tablicy

1. Upewnij się, że dwie tablice mają taką samą rangę (liczbę wymiarów), jak i zgodne typy danych elementów.

2. Użyj standardowej instrukcji przypisania, aby przypisać tablicę źródłową do tablicy docelowej. Nie Obserwuj żadnej nazwy tablicy z nawiasami.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

Po przypisaniu jednej tablicy do innej obowiązują następujące reguły:

- **Równe Range.** Ranga (liczba wymiarów) tablicy docelowej musi być taka sama jak w przypadku tablicy źródłowej.

  Jeśli Range dwóch tablic są równe, wymiary nie muszą być równe. Liczba elementów w danym wymiarze może ulec zmianie podczas przypisywania.

- **Typy elementów.** Obie tablice muszą mieć elementy *typu referencyjnego* lub obie tablice muszą mieć elementy *typu wartości* . Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](../data-types/value-types-and-reference-types.md).

  - Jeśli obie tablice mają elementy typu wartości, typy danych elementu muszą być dokładnie takie same. Jedynym wyjątkiem jest to, że można przypisać tablicę `Enum` elementów do tablicy typu podstawowego tego elementu `Enum` .

  - Jeśli obie tablice mają elementy typu referencyjnego, typ elementu źródłowego musi pochodzić od typu elementu docelowego. W takim przypadku dwie tablice mają taką samą relację dziedziczenia jak ich elementy. Jest to nazywane *kowariancją tablicową*.

Kompilator zgłasza błąd, jeśli powyższe reguły zostały naruszone, na przykład jeśli typy danych nie są zgodne lub Range nie są równe. Można dodać obsługę błędów do kodu, aby upewnić się, że tablice są zgodne przed próbą przypisania. Możesz również użyć słowa kluczowego [operatora TryCast](../../../language-reference/operators/trycast-operator.md) , jeśli chcesz uniknąć zgłaszania wyjątku.

## <a name="see-also"></a>Zobacz też

- [Tablice](index.md)
- [Rozwiązywanie problemów związanych z tablicami](troubleshooting-arrays.md)
- [Enum, instrukcja](../../../language-reference/statements/enum-statement.md)
- [Konwersje tablic](../data-types/array-conversions.md)
