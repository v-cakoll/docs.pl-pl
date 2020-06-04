---
title: 'Porady: tworzenie zmiennej, która nie zmienia wartości'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 04e08784b5cfbdeb6db73b9b00fe9afa201bd06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410519"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Porady: tworzenie zmiennej, która nie zmienia wartości (Visual Basic)

Pojęcie zmiennej, która nie zmienia jej wartości, może wydawać się sprzeczne. Istnieją jednak sytuacje, w których stała nie jest wykonalna i warto mieć zmienną o stałej wartości. W takim przypadku można zdefiniować zmienną elementu członkowskiego za pomocą słowa kluczowego [ReadOnly](../../../language-reference/modifiers/readonly.md) .

Nie można użyć [instrukcji const](../../../language-reference/statements/const-statement.md) do zadeklarowania i przypisania wartości stałej w następujących okolicznościach:

- `Const`Instrukcja nie akceptuje typu danych, którego chcesz użyć

- Nie znasz wartości w czasie kompilacji

- Nie można obliczyć wartości stałej w czasie kompilacji

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Aby utworzyć zmienną, która nie zmienia wartości

1. Na poziomie modułu należy zadeklarować zmienną członkowską przy użyciu [instrukcji Dim](../../../language-reference/statements/dim-statement.md)i dołączyć słowo kluczowe [ReadOnly](../../../language-reference/modifiers/readonly.md) .

    ```vb
    Dim ReadOnly timeStarted
    ```

    Można określić `ReadOnly` tylko dla zmiennej składowej. Oznacza to, że należy zdefiniować zmienną na poziomie modułu poza procedurą.

2. Jeśli można obliczyć wartość w pojedynczej instrukcji w czasie kompilacji, należy użyć klauzuli inicjacji w `Dim` instrukcji. Postępuj zgodnie z klauzulą [as](../../../language-reference/statements/as-clause.md) znaku równości ( `=` ), po którym następuje wyrażenie. Upewnij się, że kompilator może oszacować to wyrażenie jako wartość stałą.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Można przypisać wartość do `ReadOnly` zmiennej tylko raz. Gdy to zrobisz, żaden kod nie może zmienić jego wartości.

    Jeśli nie znasz wartości w czasie kompilacji lub nie można obliczyć jej w czasie kompilacji w jednej instrukcji, można nadal przypisać ją w czasie wykonywania w konstruktorze. Aby to zrobić, należy zadeklarować `ReadOnly` zmienną na poziomie klasy lub struktury. W konstruktorze dla tej klasy lub struktury Oblicz ustaloną wartość zmiennej i przypisz ją do zmiennej przed zwróceniem z konstruktora.

## <a name="see-also"></a>Zobacz też

- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Const, instrukcja](../../../language-reference/statements/const-statement.md)
