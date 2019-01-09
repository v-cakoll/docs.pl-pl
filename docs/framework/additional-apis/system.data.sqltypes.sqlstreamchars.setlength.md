---
title: Metoda SqlStreamChars.SetLength(Int64) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7eb2b1bfe0a3d180b54c41cbca1d645dfb402be7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152249"
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