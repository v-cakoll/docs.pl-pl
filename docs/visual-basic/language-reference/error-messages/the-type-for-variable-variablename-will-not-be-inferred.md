---
title: Typ zmiennej „<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512722"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ zmiennej "\<VariableName >" nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym

Typ zmiennej "\<VariableName >" nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym. Zmień nazwę zmiennej "\<VariableName >" lub użyj w pełni kwalifikowanej nazwy (na przykład "Me. VariableName" lub "MyBase. VariableName").

Zmienna sterująca pętli w kodzie ma taką samą nazwę jak pole klasy lub innego zakresu otaczającego. Ponieważ zmienna kontroli jest używana bez `As` klauzuli, jest ona powiązana z polem w otaczającym zakresie i kompilator nie tworzy dla niego nowej zmiennej ani nie wystawia jego typu.

W poniższym przykładzie `Index`Zmienna sterująca `For` w instrukcji jest powiązana `Customer` z `Index` polem w klasie. Kompilator nie tworzy nowej zmiennej dla zmiennej `Index` kontroli ani nie wywnioskuje jej typu.

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

Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać informacje o sposobach ukrycia ostrzeżeń lub sposobie traktowania ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**Identyfikator błędu:** BC42110

### <a name="to-address-this-warning"></a>Aby rozwiązać ten komunikat ostrzegawczy

- Ustaw zmienną sterującą pętli jako lokalną, zmieniając jej nazwę na identyfikator, który nie jest również nazwą pola klasy.

  ```vb
  For I = 1 To 10
  ```

- Wyjaśnij, że Zmienna sterująca pętli jest powiązana z polem klasy przez `Me.` prefiks do nazwy zmiennej.

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

## <a name="see-also"></a>Zobacz także

- [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
