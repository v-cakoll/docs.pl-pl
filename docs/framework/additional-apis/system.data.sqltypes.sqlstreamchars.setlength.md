---
title: Metoda SqlStreamChars.SetLength(Int64) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1283fea83cf77bbc898d460feedc72b898a65fb7
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633949"
---
# <a name="sqlstreamcharssetlengthint64-method"></a>Metoda SqlStreamChars.SetLength(Int64)

W przypadku przesłonięcia w klasie pochodnej, zwalnia zasoby używane przez strumień. Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll. Jest przeznaczony do użytku przez program SQL Server. W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a>Parametry

`value`\
Wymagana długość bieżącego strumienia, w bajtach.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `SqlStreamChars.SetLength` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Data.SqlTypes>

**Zestaw:** Dane systemowe (w System.Data.dll)

**Wersje programu .NET framework:** Dostępne od wersji 2.0.