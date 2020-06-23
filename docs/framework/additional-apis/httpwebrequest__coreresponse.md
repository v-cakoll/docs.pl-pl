---
title: HttpWebRequest. _CoreResponse — pole
description: Przeczytaj o polu HttpWebRequest. _CoreResponse w programie .NET. To pole jest obiektem CoreResponseData lub Exception zawierającym wynik analizy odpowiedzi HTTP.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989750"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest. \_ Pole CoreResponse

`HttpWebRequest._CoreResponse`jest obiektem ( [CoreResponseData](coreresponsedata.md) lub a <xref:System.Exception> ) zawierającym wynik analizy odpowiedzi HTTP.

## <a name="syntax"></a>Składnia
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Ten interfejs API nie jest przeznaczony do użycia bezpośrednio w kodzie. Zamiast tego należy użyć, <xref:System.Diagnostics.DiagnosticSource> Aby podłączyć kod sieciowy. Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)

**.NET Framework wersje:** Dostępne od 2,0.
