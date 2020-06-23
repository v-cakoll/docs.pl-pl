---
title: CoreResponseData, klasa
description: Zrozumienie klasy CoreResponseData, która reprezentuje analizę nagłówków HTTP i treść odpowiedzi. Znajduje się w przestrzeni nazw System.Net na platformie .NET.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 8248cc20f6528a1c3bc64c9b9339a3a3000d03a0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989798"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="d1f2f-104">CoreResponseData, klasa</span><span class="sxs-lookup"><span data-stu-id="d1f2f-104">CoreResponseData Class</span></span>

<span data-ttu-id="d1f2f-105">`CoreResponseData`Klasa reprezentuje analizę nagłówków HTTP i treść odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-105">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1f2f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1f2f-106">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="d1f2f-107">Ten interfejs API jest wewnętrzny i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-107">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="d1f2f-108">Zamiast tego należy użyć, <xref:System.Diagnostics.DiagnosticSource> Aby podłączyć kod sieciowy.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="d1f2f-109">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="d1f2f-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="d1f2f-110">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1f2f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1f2f-111">Requirements</span></span>

<span data-ttu-id="d1f2f-112">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d1f2f-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d1f2f-113">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="d1f2f-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d1f2f-114">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-114">**.NET Framework versions:** Available since 2.0.</span></span>
