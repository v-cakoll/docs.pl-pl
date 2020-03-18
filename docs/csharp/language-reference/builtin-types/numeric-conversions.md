---
title: Wbudowane konwersje liczbowe — odwołanie do języka C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399603"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Wbudowane konwersje liczbowe (odwołanie do języka C#)

C# zawiera zestaw [typów liczbowych integralną](integral-numeric-types.md) i [zmiennoprzecinkową.](floating-point-numeric-types.md) Istnieje konwersja między dwoma typami liczbowymi, niejawne lub jawne. Należy użyć [operatora `()` rzutowania,](../operators/type-testing-and-cast.md#cast-operator-) aby wywołać jawną konwersję.

## <a name="implicit-numeric-conversions"></a>Niejawne konwersje liczbowe

W poniższej tabeli przedstawiono wstępnie zdefiniowane konwersje niejawne między wbudowanymi typami liczbowymi:

|Z|Do|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`short``int`, `long`, `float` `double`, , lub`decimal`|
|[Bajtów](integral-numeric-types.md)|`short``ushort`, `int`, `uint` `long`, `ulong` `float`, `double`, lub`decimal`|
|[short](integral-numeric-types.md)|`int`, `long` `float`, `double`, lub`decimal`|
|[ushort](integral-numeric-types.md)|`int``uint`, `long`, `ulong` `float`, `double`, lub`decimal`|
|[int](integral-numeric-types.md)|`long`, `float` `double`, lub`decimal`|
|[Uint](integral-numeric-types.md)|`long`, `ulong` `float`, `double`, lub`decimal`|
|[long](integral-numeric-types.md)|`float`, `double`lub`decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`lub`decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Niejawne konwersje `int`z `ulong` , `float` `uint`, `long`lub `double` do iz `long` lub `ulong` do może spowodować utratę precyzji, ale nigdy nie utratę rzędu wielkości. Inne niejawne konwersje liczbowe nigdy nie tracą żadnych informacji.

Należy również pamiętać, że

- Każdy [typ liczbowy integralną](integral-numeric-types.md) jest niejawnie konwertowalny na dowolny [typ numeryczny zmiennoprzecinkowego](floating-point-numeric-types.md).

- Nie ma żadnych niejawnych `byte` `sbyte` konwersji do i typów. Nie ma żadnych niejawnych `double` `decimal` konwersji z i typów.

- Nie ma żadnych niejawnych `decimal` konwersji `float` między `double` typem a lub typami.

- Wartość wyrażenia `int` stałego typu (na przykład wartość reprezentowana przez literał całkowity) może być `sbyte`niejawnie konwertowana na , `byte`, `short` `ushort`, , `uint`lub `ulong`, jeśli mieści się w zakresie typu docelowego:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Jak pokazano w poprzednim przykładzie, jeśli wartość stała nie znajduje się w zakresie typu docelowego, występuje błąd kompilatora [CS0031.](../../misc/cs0031.md)

## <a name="explicit-numeric-conversions"></a>Jawne konwersje liczbowe

W poniższej tabeli przedstawiono wstępnie zdefiniowane jawne konwersje między wbudowanymi typami liczbowymi, dla których nie ma [konwersji niejawnej:](#implicit-numeric-conversions)

|Z|Do|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`byte`, `ushort` `uint`, lub`ulong`|
|[Bajtów](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte` `ushort`, `uint`, lub`ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`lub`short`|
|[int](integral-numeric-types.md)|`sbyte``byte`, `short`, `ushort` `uint`, , lub`ulong`|
|[Uint](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort`, lub`int`|
|[long](integral-numeric-types.md)|`sbyte``byte`, `short`, `ushort` `int`, `uint`, lub`ulong`|
|[ulong](integral-numeric-types.md)|`sbyte``byte`, `short`, `ushort` `int`, `uint`, lub`long`|
|[float](floating-point-numeric-types.md)|`sbyte``byte`, `short`, `ushort` `int`, `uint` `long`, `ulong`, lub`decimal`|
|[double](floating-point-numeric-types.md)|`sbyte``byte`, `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , lub`decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte``byte`, `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , lub`double`|

> [!NOTE]
> Jawna konwersja liczbowa może spowodować utratę danych <xref:System.OverflowException>lub zgłosić wyjątek, zazwyczaj .

Należy również pamiętać, że

- Podczas konwertowania wartości typu integralnego na inny typ integralną wynik zależy od [kontekstu sprawdzania](../keywords/checked-and-unchecked.md)przepełnienia. W zaznaczonym kontekście konwersja powiedzie się, jeśli wartość źródłowa znajduje się w zakresie typu docelowego. W przeciwnym <xref:System.OverflowException> razie zostanie wyrzucony. W niesprawdzonym kontekście konwersja zawsze powiodła się i przebiega w następujący sposób:

  - Jeśli typ źródła jest większy niż typ docelowy, wartość źródłowa jest obcinana przez odrzucenie jego "dodatkowych" najbardziej znaczących bitów. Wynik jest następnie traktowany jako wartość typu docelowego.

  - Jeśli typ źródła jest mniejszy niż typ docelowy, wartość źródłowa jest rozszerzona znakiem lub zerowa, dzięki czemu ma taki sam rozmiar jak typ docelowy. Sign-extension jest używany, jeśli typ źródła jest podpisany; zero-extension jest używany, jeśli typ źródła jest niepodpisany. Wynik jest następnie traktowany jako wartość typu docelowego.

  - Jeśli typ źródła ma taki sam rozmiar jak typ docelowy, wartość źródłowa jest traktowana jako wartość typu docelowego.

- Podczas konwertowania `decimal` wartości na typ całą literę wartość ta jest zaokrąglana w kierunku zera do najbliższej wartości integralnej. Jeśli wynikowa wartość całkowita znajduje się poza <xref:System.OverflowException> zakresem typu docelowego, zgłaszany jest a.

- Podczas konwertowania `double` `float` lub wartości na typ całą literę, ta wartość jest zaokrąglana w kierunku zera do najbliższej wartości całkowej. Jeśli wynikowa wartość całkowita znajduje się poza zakresem typu docelowego, wynik zależy od [kontekstu sprawdzania](../keywords/checked-and-unchecked.md)przepełnienia . W kontekście zaznaczonym jest <xref:System.OverflowException> generowany, podczas gdy w niezaznaczonej kontekście wynik jest nieokreśloną wartością typu docelowego.

- Podczas konwersji `double` `float`na `double` wartość jest zaokrąglana do najbliższej `float` wartości. Jeśli `double` wartość jest zbyt mała lub zbyt `float` duża, aby zmieścić się w typie, wynik wynosi zero lub nieskończoność.

- Podczas `float` konwertowania `double` `decimal`lub do , wartość `decimal` źródłowa jest konwertowana na reprezentację i zaokrąglana do najbliższej liczby po 28 miejscu po przecinku, jeśli jest to wymagane. W zależności od wartości wartości źródłowej może wystąpić jeden z następujących wyników:

  - Jeśli wartość źródłowa jest zbyt mała, aby można ją było przedstawić jako `decimal`wynik, wynik staje się zerowy.

  - Jeśli wartość źródłowa jest NaN (nie liczba), nieskończoność lub `decimal`zbyt <xref:System.OverflowException> duże, aby być reprezentowane jako , jest generowany.

- `decimal` Podczas konwertowania `float` `double`na lub wartość źródłowa `float` jest `double` zaokrąglana odpowiednio do najbliższej lub wartości.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Niejawne konwersje liczbowe](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Jawne konwersje liczbowe](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Konwersje rzutowania i typu](../../programming-guide/types/casting-and-type-conversions.md)
