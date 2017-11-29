---
title: Pole ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable pola

`ServicePointManager.s_ServicePointTable`jest <xref:System.Collections.Hashtable> zawierający listę aktywnych połączeń HTTP (<xref:System.Net.ServicePoint>s) w <xref:System.AppDomain>.

## <a name="syntax"></a>Składnia
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Pole jest prywatny i nie są one przeznaczone do użycia bezpośrednio w kodzie.
> 
> Firma Microsoft obsługuje Użyj tego pola w aplikacji produkcyjnej, w żadnym przypadku.

## <a name="requirements"></a>Wymagania

**Namespace:**<xref:System.Net>

**Zestaw:** System (w System.dll)

**Wersje programu .NET framework:** dostępne od wersji 2.0.
