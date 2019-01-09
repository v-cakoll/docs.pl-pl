---
title: Metoda SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: aab3195ec0d300a7f001f98f2d646c85be939356
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152186"
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