---
title: 'Instrukcje: Przypisywanie tablicy do innej tablicy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: a39888f19e5033a5c6622313fb7451d6463b2f7c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64858885"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Instrukcje: Przypisywanie tablicy do innej tablicy (Visual Basic)

Ponieważ tablice są obiektami, będziesz ich używać w instrukcji przypisania, podobnie jak inne typy obiektów. Zmienną tablicową mieści wskaźnik do danych stanowiące elementów tablicy i informacji Ranga i długość i przypisania kopiuje tylko ten wskaźnik.

### <a name="to-assign-one-array-to-another-array"></a>Aby przypisać jednej tablicy do innej tablicy

1. Upewnij się, że dwie tablice mają tę samą rangę (liczba wymiarów) i typy danych zgodne elementu.

2. Używać instrukcji przypisania standardowych można przypisać tablica źródłowa do tablicy docelowej. Nie wykonuj obu nazwa tablicy za pomocą nawiasów.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

Podczas przypisywania tablicy do innej, obowiązują następujące reguły:

- **Równe rangę.** Ranga tablicy docelowej (liczba wymiarów) musi być taka sama jak tablica źródłowa.

  Podana rangę dwie tablice są równe, wymiary nie są równe. Liczba elementów w określonym wymiarze, które można zmienić podczas przypisywania.

- **Typy elementów.** Musi mieć albo obu tablicach *odwołania do typu* elementów lub obu tablicach, musi mieć *typu wartości* elementów. Aby uzyskać więcej informacji, zobacz [typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).

  - Jeśli elementy typu wartości obu tablicach, typów danych elementów musi być dokładnie takie same. Jedynym wyjątkiem jest, którą można przypisać tablicę `Enum` elementów do tablicy typu podstawowego `Enum`.

  - Jeśli obu tablicach ma odwołanie do typu elementów, typ elementu źródłowego musi pochodzić od typu elementu docelowego. W przypadku dwóch tablic mają ten sam relację dziedziczenia jako ich elementy. Jest to nazywane *Kowariancja tablicy*.

Kompilator zgłasza błąd, jeśli powyższe zasady są naruszone, na przykład jeśli typy danych nie są zgodne lub rangę są nierówne. Możesz dodać obsługę błędów do kodu w taki sposób, aby upewnić się, że tablice są zgodne, przed podjęciem próby wykonania przypisania. Można również użyć [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) — słowo kluczowe, jeśli chcesz uniknąć, zostanie zgłoszony wyjątek.

## <a name="see-also"></a>Zobacz także

- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
