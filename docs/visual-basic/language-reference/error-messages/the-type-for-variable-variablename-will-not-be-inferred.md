---
title: Typ zmiennej „<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 98aeb5699fdd5e5e538a205acd37436019c3fc03
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363049"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ zmiennej „\<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym

Typ zmiennej " \<variablename> " nie zostanie wywnioskowany, ponieważ jest powiązany z polem w otaczającym zakresie. Zmień nazwę " \<variablename> " lub użyj w pełni kwalifikowanej nazwy (na przykład "Me. VariableName" lub "MyBase. VariableName").

Zmienna sterująca pętli w kodzie ma taką samą nazwę jak pole klasy lub innego zakresu otaczającego. Ponieważ zmienna kontroli jest używana bez `As` klauzuli, jest ona powiązana z polem w otaczającym zakresie i kompilator nie tworzy dla niego nowej zmiennej ani nie wystawia jego typu.

W poniższym przykładzie `Index` Zmienna sterująca w `For` instrukcji jest powiązana z `Index` polem w `Customer` klasie. Kompilator nie tworzy nowej zmiennej dla zmiennej kontroli `Index` ani nie wywnioskuje jej typu.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje o sposobach ukrycia ostrzeżeń lub sposobie traktowania ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**Identyfikator błędu:** BC42110

### <a name="to-address-this-warning"></a>Aby rozwiązać ten komunikat ostrzegawczy

- Ustaw zmienną sterującą pętli jako lokalną, zmieniając jej nazwę na identyfikator, który nie jest również nazwą pola klasy.

  ```vb
  For I = 1 To 10
  ```

- Wyjaśnij, że Zmienna sterująca pętli jest powiązana z polem klasy przez prefiks `Me.` do nazwy zmiennej.

  ```vb
  For Me.Index = 1 To 10
  ```

- Zamiast polegać na wnioskach o typie lokalnym, należy użyć `As` klauzuli, aby określić typ dla zmiennej kontroli pętli.

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>Przykład
 Poniższy kod ilustruje poprzedni przykład przy pierwszej korekcie.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a>Zobacz też

- [Option Infer — Instrukcja](../statements/option-infer-statement.md)
- [For Each...Next, instrukcja](../statements/for-each-next-statement.md)
- [For...Next, instrukcja](../statements/for-next-statement.md)
- [Instrukcje: odwoływanie się do bieżącego wystąpienia obiektu](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase i MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
