---
title: SqlStreamChars.Flush Method (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8cd24a5ca420552f283da61ecd4edcad02965403
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705860"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="d4e0f-102">SqlStreamChars.Flush Method</span><span class="sxs-lookup"><span data-stu-id="d4e0f-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="d4e0f-103">W przypadku przesłonięcia w klasie pochodnej, czyści wszystkie bufory tego strumienia i powoduje, że wszystkie buforowane dane są zapisywane w odpowiednie urządzenia.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="d4e0f-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d4e0f-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d4e0f-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4e0f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4e0f-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="d4e0f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4e0f-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d4e0f-109">`SqlStreamChars.Flush` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d4e0f-110">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d4e0f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4e0f-111">Requirements</span></span>

<span data-ttu-id="d4e0f-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d4e0f-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d4e0f-113">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d4e0f-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d4e0f-114">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="d4e0f-114">**.NET Framework versions:** Available since 2.0.</span></span>