---
title: 'Porady: określanie, do jakiego typu odnosi się zmienna obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: d3224000f5958a8619e38c4d2f6dc5dbb275ad45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410493"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)

Zmienna obiektu zawiera wskaźnik do danych, które są przechowywane w innym miejscu. Typ tych danych może ulec zmianie w czasie wykonywania. W dowolnym momencie można użyć <xref:System.Type.GetTypeCode%2A> metody w celu określenia bieżącego typu uruchomieniowego lub [operatora typeof](../../../language-reference/operators/typeof-operator.md) , aby dowiedzieć się, czy bieżący typ czasu wykonywania jest zgodny z określonym typem.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Aby określić dokładny typ, do którego odwołuje się zmienna obiektu

1. Na zmiennej obiektu Wywołaj metodę, <xref:System.Object.GetType%2A> Aby pobrać <xref:System.Type?displayProperty=nameWithType> obiekt.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. Na <xref:System.Type?displayProperty=nameWithType> klasie Wywołaj metodę Shared, <xref:System.Type.GetTypeCode%2A> Aby pobrać <xref:System.TypeCode> wartość wyliczenia dla typu obiektu.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Możesz przetestować <xref:System.TypeCode> wartość wyliczenia dla niezależnych elementów członkowskich wyliczenia, takich jak `Double` .

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Aby określić, czy typ zmiennej obiektu jest zgodny z określonym typem

- Użyj `TypeOf` operatora w połączeniu z [operatorem is](../../../language-reference/operators/is-operator.md) , aby przetestować obiekt za pomocą `TypeOf` wyrażenia... `Is` .

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`Wyrażenie... `Is` zwraca wartość, `True` Jeśli typ czasu wykonywania obiektu jest zgodny z określonym typem.

    Kryterium zgodności zależy od tego, czy określony typ jest klasą, strukturą lub interfejsem. Ogólnie rzecz biorąc, typy są zgodne, jeśli obiekt jest tego samego typu co, dziedziczy po lub implementuje określony typ. Aby uzyskać więcej informacji, zobacz [operator typeof](../../../language-reference/operators/typeof-operator.md).

## <a name="compile-the-code"></a>Kompiluj kod

Należy zauważyć, że określony typ nie może być zmienną ani wyrażeniem. Musi to być nazwa typu zdefiniowanego, na przykład klasy, struktury lub interfejsu. Obejmuje to typy wewnętrzne, takie jak `Integer` i `String` .

## <a name="see-also"></a>Zobacz też

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Zmienne obiektów](object-variables.md)
- [Wartości zmiennej obiektu](object-variable-values.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
