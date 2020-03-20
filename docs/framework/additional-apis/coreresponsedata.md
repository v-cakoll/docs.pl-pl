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
ms.openlocfilehash: 39a14a3df5059cc47cd4879e4d4ba351cc7b655b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156119"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="d6c53-102">CoreResponseData, klasa</span><span class="sxs-lookup"><span data-stu-id="d6c53-102">CoreResponseData Class</span></span>

<span data-ttu-id="d6c53-103">Klasa `CoreResponseData` reprezentuje analizowanie nagłówków HTTP i treści odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d6c53-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6c53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6c53-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="d6c53-105">Ten interfejs API jest wewnętrzny i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d6c53-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="d6c53-106">Zamiast tego należy użyć <xref:System.Diagnostics.DiagnosticSource> do hakowania kodu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="d6c53-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="d6c53-107">Zobacz [DiagnosticSource Podręcznik użytkownika](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="d6c53-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="d6c53-108">Firma Microsoft nie obsługuje użycia tej klasy w aplikacji produkcyjnej w żadnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="d6c53-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c53-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6c53-109">Requirements</span></span>

<span data-ttu-id="d6c53-110">**Obszar nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d6c53-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d6c53-111">**Montaż:** System (w pliku System.dll)</span><span class="sxs-lookup"><span data-stu-id="d6c53-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d6c53-112">**Wersje programu .NET Framework:** Dostępne od 2.0.</span><span class="sxs-lookup"><span data-stu-id="d6c53-112">**.NET Framework versions:** Available since 2.0.</span></span>
