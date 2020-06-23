---
title: CoreResponseData. m_ResponseHeaders — pole
description: Zapoznaj się z polem CoreResponseData. m_ResponseHeaders w programie .NET. To pole jest typu WebHeaderCollection z nagłówkami skojarzonymi z odpowiedzią serwera.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989792"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="3c174-104">CoreResponseData. m \_ ResponseHeaders pole</span><span class="sxs-lookup"><span data-stu-id="3c174-104">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="3c174-105">`CoreResponseData.m_ResponseHeaders`jest <xref:System.Net.WebHeaderCollection> nagłówkami skojarzonymi z odpowiedzią serwera.</span><span class="sxs-lookup"><span data-stu-id="3c174-105">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c174-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c174-106">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="3c174-107">Ten interfejs API nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c174-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="3c174-108">Zamiast tego należy użyć, <xref:System.Diagnostics.DiagnosticSource> Aby podłączyć kod sieciowy.</span><span class="sxs-lookup"><span data-stu-id="3c174-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="3c174-109">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="3c174-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="3c174-110">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="3c174-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3c174-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c174-111">Requirements</span></span>

<span data-ttu-id="3c174-112">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="3c174-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="3c174-113">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="3c174-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="3c174-114">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="3c174-114">**.NET Framework versions:** Available since 2.0.</span></span>
