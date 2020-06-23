---
title: ComNetOS, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990402"
---
# <a name="comnetos-class"></a><span data-ttu-id="19202-102">ComNetOS, klasa</span><span class="sxs-lookup"><span data-stu-id="19202-102">ComNetOS class</span></span>

<span data-ttu-id="19202-103">Zawiera informacje o bieżącym systemie operacyjnym, takie jak jego wersja i typ instalacji (klient lub serwer).</span><span class="sxs-lookup"><span data-stu-id="19202-103">Provides information about the current operating system, such as its version and installation type (client or server).</span></span> <span data-ttu-id="19202-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="19202-104">This class cannot be inherited.</span></span>
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> <span data-ttu-id="19202-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="19202-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="19202-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="19202-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="iswin7orlater-field"></a><span data-ttu-id="19202-107">Pole IsWin7orLater</span><span class="sxs-lookup"><span data-stu-id="19202-107">IsWin7orLater field</span></span>

<span data-ttu-id="19202-108">Określa, czy wersja systemu operacyjnego to Windows 7, czy nowsza.</span><span class="sxs-lookup"><span data-stu-id="19202-108">Specifies whether the operating system version is Windows 7 or later.</span></span>

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a><span data-ttu-id="19202-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19202-109">Requirements</span></span>

<span data-ttu-id="19202-110">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="19202-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="19202-111">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="19202-111">**Assembly:** System (in System.dll)</span></span>
