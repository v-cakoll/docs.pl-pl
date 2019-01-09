---
title: Metoda SqlStreamChars.Write (Char [], Int32, Int32) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: e8c8ee7ab7a744c1a1d18212f1c7f9788c91ea0d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152192"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>Metoda SqlStreamChars.Write (Char [], Int32, Int32)

W przypadku przesłonięcia w klasie pochodnej, zapisuje sekwencji znaków do bieżącego strumienia i przesuwa bieżącą pozycję w tym strumieniu według liczby znaków zapisanych. Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll. Jest przeznaczony do użytku przez program SQL Server. W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametry

`buffer`  
Tablicy znaków do zapisania.

`offset`  
Przesunięcie względem źródła.

`count`  
Liczba znaków, które mają być zapisywane do strumienia bieżącego.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `SqlStreamChars.Write` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Data.SqlTypes>

**Zestaw:** Dane systemowe (w System.Data.dll)

**Wersje programu .NET framework:** Dostępne od wersji 2.0.