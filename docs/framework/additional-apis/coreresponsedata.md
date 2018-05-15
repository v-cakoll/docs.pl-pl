---
title: Klasa CoreResponseData
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
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="1a549-102">Klasa CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="1a549-102">CoreResponseData Class</span></span>

<span data-ttu-id="1a549-103">`CoreResponseData` Klasa reprezentuje podczas analizowania nagłówków HTTP i treści odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1a549-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a549-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a549-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="1a549-105">Ten interfejs API jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a549-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="1a549-106">Zamiast tego należy używać <xref:System.Diagnostics.DiagnosticSource> na połączeniu sieci kodu.</span><span class="sxs-lookup"><span data-stu-id="1a549-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="1a549-107">Zobacz [Podręcznik użytkownika DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="1a549-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="1a549-108">Microsoft w aplikacji produkcyjnej, w żadnym przypadku nie obsługuje korzystanie z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1a549-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a549-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a549-109">Requirements</span></span>

<span data-ttu-id="1a549-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="1a549-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="1a549-111">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="1a549-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="1a549-112">**Wersje programu .NET framework:** dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="1a549-112">**.NET Framework versions:** Available since 2.0.</span></span>
