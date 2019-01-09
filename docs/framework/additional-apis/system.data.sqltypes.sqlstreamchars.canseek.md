---
title: Właściwość SqlStreamChars.CanSeek (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 0145fe87e2c8aa3dd40e73f0089fe40b6b6cca30
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152240"
---
# <a name="sqlstreamcharscanseek-property"></a>Właściwość SqlStreamChars.CanSeek

W przypadku przesłonięcia w klasie pochodnej pobiera wartość wskazującą, czy bieżący strumień obsługuje operacji wyszukiwania. Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll. Jest przeznaczony do użytku przez program SQL Server. W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Wartość właściwości

<xref:System.Boolean>\
`true` Jeśli bieżący strumień obsługuje operacji wyszukiwania; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `SqlStreamChars.CanSeek` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Data.SqlTypes>

**Zestaw:** Dane systemowe (w System.Data.dll)

**Wersje programu .NET framework:** Dostępne od wersji 2.0.