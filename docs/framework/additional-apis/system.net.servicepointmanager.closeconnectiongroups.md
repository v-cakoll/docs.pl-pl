---
title: ServicePointManager. CloseConnectionGroups — Metoda (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990365"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="87e13-102">ServicePointManager. CloseConnectionGroups — Metoda</span><span class="sxs-lookup"><span data-stu-id="87e13-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="87e13-103">Wykonuje iterację we wszystkich punktach usługi i zamyka grupy połączeń o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="87e13-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="87e13-104">Ta metoda jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="87e13-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="87e13-105">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="87e13-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="87e13-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87e13-106">Parameters</span></span>

<span data-ttu-id="87e13-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="87e13-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="87e13-108">Nazwa grupy połączeń do zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="87e13-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="87e13-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87e13-109">Requirements</span></span>

<span data-ttu-id="87e13-110">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="87e13-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="87e13-111">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="87e13-111">**Assembly:** System (in System.dll)</span></span>
