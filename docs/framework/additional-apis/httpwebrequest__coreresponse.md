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
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356202"
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="41b72-102">HttpWebRequest. \_CoreResponse pola</span><span class="sxs-lookup"><span data-stu-id="41b72-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="41b72-103">`HttpWebRequest._CoreResponse` obiekt (albo [CoreResponseData](coreresponsedata.md) lub <xref:System.Exception>) zawierający wynik analizy odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="41b72-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="41b72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41b72-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="41b72-105">Ten interfejs API nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="41b72-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="41b72-106">Zamiast tego należy używać <xref:System.Diagnostics.DiagnosticSource> na połączeniu sieci kodu.</span><span class="sxs-lookup"><span data-stu-id="41b72-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="41b72-107">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="41b72-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="41b72-108">Microsoft w aplikacji produkcyjnej, w żadnym przypadku nie obsługuje korzystanie z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="41b72-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="41b72-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41b72-109">Requirements</span></span>

<span data-ttu-id="41b72-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="41b72-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="41b72-111">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="41b72-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="41b72-112">**Wersje programu .NET framework:** dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="41b72-112">**.NET Framework versions:** Available since 2.0.</span></span>
