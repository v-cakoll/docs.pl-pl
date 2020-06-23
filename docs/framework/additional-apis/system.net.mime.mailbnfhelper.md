---
title: MailBnfHelper, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990370"
---
# <a name="mailbnfhelper-class"></a>MailBnfHelper, klasa

Zawiera metody narzędzi do analizowania ciągów w formacie internetowym. Klasa ta nie może być dziedziczona.

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="ascii7bitmaxvalue-field"></a>Pole Ascii7bitMaxValue

Reprezentuje maksymalną 7-bitową wartość ASCII.

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a>Pole aText

Reprezentuje znaki dozwolone w atomach.

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a>Pole CR

Reprezentuje znak powrotu karetki.

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a>Pole CTEXT

Reprezentuje znaki dozwolone wewnątrz komentarzy.

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a>Pole dot

Reprezentuje znak pełny-Stop ( `.` ).

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a>Pole EndComment

Reprezentuje znak, który określa koniec komentarza.

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a>Pole LF

Reprezentuje znak wysuwu wiersza.

```csharp
internal static readonly char LF
```

## <a name="space-field"></a>Pole przestrzeni

Reprezentuje znak spacji.

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a>Pole StartComment

Reprezentuje znak określający początek komentarza.

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a>Pole tabulacji

Reprezentuje znak tabulacji.

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
