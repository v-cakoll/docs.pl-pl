---
title: 'Porady: dostęp do elementów członkowskich obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410545"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Porady: dostęp do elementów członkowskich obiektu (Visual Basic)

Gdy masz zmienną obiektu, która odwołuje się do obiektu, często chcesz współpracować z elementami członkowskimi tego obiektu, takimi jak metody, właściwości, pola i zdarzenia. Na przykład po utworzeniu nowego <xref:System.Windows.Forms.Form> obiektu można ustawić jego <xref:System.Windows.Forms.Control.Text%2A> Właściwość lub wywołać <xref:System.Windows.Forms.Control.Focus%2A> metodę.

## <a name="accessing-members"></a>Dostęp do członków

Dostęp do elementów członkowskich obiektu można uzyskać za pomocą zmiennej, która odwołuje się do niej.

#### <a name="to-access-members-of-an-object"></a>Aby uzyskać dostęp do elementów członkowskich obiektu

- Użyj operatora dostępu do elementów członkowskich ( `.` ) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.

    ```vb
    currentText = newForm.Text
    ```

    Jeśli element członkowski jest [współużytkowany](../../../language-reference/modifiers/shared.md), nie potrzebujesz zmiennej, aby uzyskać do niej dostęp.

## <a name="accessing-members-of-an-object-of-known-type"></a>Uzyskiwanie dostępu do elementów członkowskich obiektu znanego typu

Jeśli znasz typ obiektu w czasie kompilacji, możesz użyć *wczesnego powiązania* dla zmiennej, która odwołuje się do niej.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Aby uzyskać dostęp do elementów członkowskich obiektu, dla którego znasz typ w czasie kompilacji

1. Zadeklaruj zmienną obiektu jako typ obiektu, który ma zostać przypisany do zmiennej.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    Za pomocą `Option Strict On` można przypisywać tylko <xref:System.Windows.Forms.Form> obiekty (lub obiekty typu pochodnego od <xref:System.Windows.Forms.Form> ) do `extraForm` . Jeśli zdefiniowano klasę lub strukturę z `CType` konwersją rozszerzającą do <xref:System.Windows.Forms.Form> , można także przypisać tę klasę lub strukturę do `extraForm` .

2. Użyj operatora dostępu do elementów członkowskich ( `.` ) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.

    ```vb
    extraForm.Show()
    ```

    Można uzyskać dostęp do wszystkich metod i właściwości specyficznych dla <xref:System.Windows.Forms.Form> klasy, niezależnie od tego, co to `Option Strict` jest ustawienie.

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Uzyskiwanie dostępu do elementów członkowskich obiektu nieznanego typu

Jeśli nie znasz typu obiektu w czasie kompilacji, musisz użyć *późnego wiązania* dla każdej zmiennej, która odwołuje się do niej.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Aby uzyskać dostęp do elementów członkowskich obiektu, dla którego nie znasz typu w czasie kompilacji

1. Zadeklaruj zmienną obiektu jako [Typ danych obiektu](../../../language-reference/data-types/object-data-type.md). (Deklarując zmienną tak `Object` samo jak deklarującą ją jako <xref:System.Object?displayProperty=nameWithType> ).

    ```vb
    Dim someControl As Object
    ```

    W programie `Option Strict On` można uzyskać dostęp tylko do elementów członkowskich, które są zdefiniowane w <xref:System.Object> klasie.

2. Użyj operatora dostępu do elementów członkowskich ( `.` ) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.

    ```vb
    someControl.GetType()
    ```

    Aby można było uzyskać dostęp do elementów członkowskich dowolnego obiektu, który jest przypisany do zmiennej obiektu, należy ustawić `Option Strict Off` . Gdy to zrobisz, kompilator nie może zagwarantować, że dany element członkowski jest uwidoczniony przez obiekt przypisany do zmiennej. Jeśli obiekt nie ujawnia elementu członkowskiego, do którego próbujesz uzyskać dostęp, <xref:System.MemberAccessException> wystąpi wyjątek.

## <a name="see-also"></a>Zobacz też

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Zmienne obiektów](object-variables.md)
- [Deklaracja zmiennej obiektu](object-variable-declaration.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
