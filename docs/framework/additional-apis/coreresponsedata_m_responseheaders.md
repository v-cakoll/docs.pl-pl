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
# <a name="coreresponsedatam_responseheaders-field"></a>CoreResponseData. m \_ ResponseHeaders pole

`CoreResponseData.m_ResponseHeaders`jest <xref:System.Net.WebHeaderCollection> nagłówkami skojarzonymi z odpowiedzią serwera.

## <a name="syntax"></a>Składnia
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> Ten interfejs API nie jest przeznaczony do użycia bezpośrednio w kodzie. Zamiast tego należy użyć, <xref:System.Diagnostics.DiagnosticSource> Aby podłączyć kod sieciowy. Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)

**.NET Framework wersje:** Dostępne od 2,0.
