---
title: 'Porady: określanie, do jakiego typu odnosi się zmienna obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 9f9b89e2fea0bd69cba6d50fa1d1fb9cc3927685
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348616"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)

Zmienna obiektu zawiera wskaźnik do danych, które są przechowywane w innym miejscu. Typ tych danych może ulec zmianie w czasie wykonywania. W dowolnym momencie można użyć metody <xref:System.Type.GetTypeCode%2A>, aby określić bieżący typ uruchomieniowy lub [operator typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) , aby dowiedzieć się, czy bieżący typ czasu wykonywania jest zgodny z określonym typem.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Aby określić dokładny typ, do którego odwołuje się zmienna obiektu

1. Na zmiennej obiektu Wywołaj metodę <xref:System.Object.GetType%2A>, aby pobrać obiekt <xref:System.Type?displayProperty=nameWithType>.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. W klasie <xref:System.Type?displayProperty=nameWithType> Wywołaj <xref:System.Type.GetTypeCode%2A> metody udostępnionej, aby pobrać <xref:System.TypeCode> wartość wyliczenia dla typu obiektu.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Można testować <xref:System.TypeCode> wartość wyliczenia dla elementów członkowskich wyliczenia, które są istotne, takich jak `Double`.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Aby określić, czy typ zmiennej obiektu jest zgodny z określonym typem

- Użyj operatora `TypeOf` w połączeniu z [operatorem is](../../../../visual-basic/language-reference/operators/is-operator.md) , aby przetestować obiekt za pomocą wyrażenia `TypeOf`...`Is`.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    Wyrażenie `TypeOf`...`Is` zwraca `True`, jeśli typ czasu wykonywania obiektu jest zgodny z określonym typem.

    Kryterium zgodności zależy od tego, czy określony typ jest klasą, strukturą lub interfejsem. Ogólnie rzecz biorąc, typy są zgodne, jeśli obiekt jest tego samego typu co, dziedziczy po lub implementuje określony typ. Aby uzyskać więcej informacji, zobacz [operator typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Należy zauważyć, że określony typ nie może być zmienną ani wyrażeniem. Musi to być nazwa typu zdefiniowanego, na przykład klasy, struktury lub interfejsu. Obejmuje to typy wewnętrzne, takie jak `Integer` i `String`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
