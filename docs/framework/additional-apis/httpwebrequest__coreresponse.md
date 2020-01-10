---
title: HttpWebRequest._CoreResponse Field
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
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740444"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="73ae2-102">HttpWebRequest.\_pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="73ae2-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="73ae2-103">`HttpWebRequest._CoreResponse` jest obiektem ( [CoreResponseData](coreresponsedata.md) lub <xref:System.Exception>) zawierającym wynik analizy odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="73ae2-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="73ae2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73ae2-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="73ae2-105">Ten interfejs API nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="73ae2-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="73ae2-106">Zamiast tego należy użyć <xref:System.Diagnostics.DiagnosticSource>, aby podłączyć kod sieciowy.</span><span class="sxs-lookup"><span data-stu-id="73ae2-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="73ae2-107">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="73ae2-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="73ae2-108">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="73ae2-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="73ae2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73ae2-109">Requirements</span></span>

<span data-ttu-id="73ae2-110">**Przestrzeń nazw:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="73ae2-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="73ae2-111">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="73ae2-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="73ae2-112">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="73ae2-112">**.NET Framework versions:** Available since 2.0.</span></span>
