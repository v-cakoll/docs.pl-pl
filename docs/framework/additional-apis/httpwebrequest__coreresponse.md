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
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="e2a2c-104">HttpWebRequest. \_ Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="e2a2c-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="e2a2c-105">`HttpWebRequest._CoreResponse`jest obiektem ( [CoreResponseData](coreresponsedata.md) lub a <xref:System.Exception> ) zawierającym wynik analizy odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2a2c-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2a2c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2a2c-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="e2a2c-107">Ten interfejs API nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e2a2c-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="e2a2c-108">Zamiast tego należy użyć, <xref:System.Diagnostics.DiagnosticSource> Aby podłączyć kod sieciowy.</span><span class="sxs-lookup"><span data-stu-id="e2a2c-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="e2a2c-109">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="e2a2c-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="e2a2c-110">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="e2a2c-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2a2c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2a2c-111">Requirements</span></span>

<span data-ttu-id="e2a2c-112">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e2a2c-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e2a2c-113">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="e2a2c-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e2a2c-114">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="e2a2c-114">**.NET Framework versions:** Available since 2.0.</span></span>
