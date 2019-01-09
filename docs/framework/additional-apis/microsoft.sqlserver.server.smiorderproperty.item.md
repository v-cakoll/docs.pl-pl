---
title: Właściwość SmiOrderProperty.Item (Microsoft.SqlServer.Server)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c586d07e8ea0c2ac0b1efb603e8900d681fd0a91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152219"
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