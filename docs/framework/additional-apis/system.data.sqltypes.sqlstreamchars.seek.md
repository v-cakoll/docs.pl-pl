---
title: Metoda SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 6f802428a73f229e948099788ec21f07efbfab76
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634521"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>Metoda SqlStreamChars.Seek (Int64, SeekOrigin)

W przypadku przesłonięcia w klasie pochodnej, Ustawia położenie w obrębie bieżącego strumienia. Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll. Jest przeznaczony do użytku przez program SQL Server. W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parametry

`offset`\
Przesunięcie bajtów, względem `origin`.

`origin`\
Jedna z wartości wyliczenia, które wskazuje punkt odniesienia, z którego można uzyskać nowe miejsce.

## <a name="returns"></a>Zwraca

<xref:System.Int32>\
Nowa pozycja w ciągu bieżącego strumienia.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `SqlStreamChars.Seek` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Data.SqlTypes>

**Zestaw:** Dane systemowe (w System.Data.dll)

**Wersje programu .NET framework:** Dostępne od wersji 2.0.