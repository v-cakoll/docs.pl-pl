---
title: CoreResponseData, klasa
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
ms.openlocfilehash: fd0ffb982c22b0a8b6cb5dd677faafb9921bf5d9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741020"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="5d7dc-102">CoreResponseData, klasa</span><span class="sxs-lookup"><span data-stu-id="5d7dc-102">CoreResponseData Class</span></span>

<span data-ttu-id="5d7dc-103">Klasa `CoreResponseData` reprezentuje analizę nagłówków HTTP i treść odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5d7dc-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d7dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d7dc-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="5d7dc-105">Ten interfejs API jest wewnętrzny i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d7dc-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="5d7dc-106">Zamiast tego należy użyć <xref:System.Diagnostics.DiagnosticSource>, aby podłączyć kod sieciowy.</span><span class="sxs-lookup"><span data-stu-id="5d7dc-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="5d7dc-107">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="5d7dc-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="5d7dc-108">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="5d7dc-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d7dc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d7dc-109">Requirements</span></span>

<span data-ttu-id="5d7dc-110">**Przestrzeń nazw:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5d7dc-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5d7dc-111">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="5d7dc-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="5d7dc-112">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="5d7dc-112">**.NET Framework versions:** Available since 2.0.</span></span>
