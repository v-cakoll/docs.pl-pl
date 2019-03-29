---
title: SmiOrderProperty.Item Property (Microsoft.SqlServer.Server)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 499522a11cac744c14ac32cf3bfe485a46b19d93
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634326"
---
# <a name="smiorderpropertyitem-property"></a>Właściwość SmiOrderProperty.Item

Pobiera kolejność kolumn dla tej jednostki. Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll. Jest przeznaczony do użytku przez program SQL Server. W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.

## <a name="syntax"></a>Składnia

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a>Wartość właściwości

Kolejność kolumn.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `SmiOrderProperty.Item` Właściwość jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje użycie tej właściwości w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:Microsoft.SqlServer.Server>

**Zestaw:** Dane systemowe (w System.Data.dll)

**Wersje programu .NET framework:** Dostępne od wersji 2.0.