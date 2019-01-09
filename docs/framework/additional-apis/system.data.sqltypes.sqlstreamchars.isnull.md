---
title: Właściwość SqlStreamChars.IsNull (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 79ebb9ec54185a94cb95dfd0fb2929e61cf513ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152207"
---
# <a name="sqlstreamcharsisnull-property"></a>Właściwość SqlStreamChars.IsNull

W przypadku przesłonięcia w klasie pochodnej pobiera wartość wskazującą, czy strumień jest `null`. Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll. Jest przeznaczony do użytku przez program SQL Server. W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.

## <a name="syntax"></a>Składnia

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Wartość właściwości

<xref:System.Boolean>\
`true` Jeśli strumień jest `null`; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `SqlStreamChars.IsNull` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Data.SqlTypes>

**Zestaw:** Dane systemowe (w System.Data.dll)

**Wersje programu .NET framework:** Dostępne od wersji 2.0.