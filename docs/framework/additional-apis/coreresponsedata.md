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
ms.openlocfilehash: 640a925c3aec86b4743b1b2b62eb3793af1cc0bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675419"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="5495b-102">CoreResponseData, klasa</span><span class="sxs-lookup"><span data-stu-id="5495b-102">CoreResponseData Class</span></span>

<span data-ttu-id="5495b-103">`CoreResponseData` Klasa reprezentuje podczas analizowania nagłówków HTTP i treści odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5495b-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="5495b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5495b-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="5495b-105">Ten interfejs API jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5495b-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="5495b-106">Zamiast tego należy używać <xref:System.Diagnostics.DiagnosticSource> można dołączyć kod sieci.</span><span class="sxs-lookup"><span data-stu-id="5495b-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="5495b-107">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="5495b-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="5495b-108">Firma Microsoft nie obsługuje użycia tej klasy w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="5495b-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5495b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5495b-109">Requirements</span></span>

<span data-ttu-id="5495b-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5495b-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5495b-111">**Zestaw:** System (System.dll)</span><span class="sxs-lookup"><span data-stu-id="5495b-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="5495b-112">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="5495b-112">**.NET Framework versions:** Available since 2.0.</span></span>
