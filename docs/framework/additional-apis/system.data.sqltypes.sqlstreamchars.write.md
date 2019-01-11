---
title: Metoda SqlStreamChars.Write (Char [], Int32, Int32) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221911"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="26093-102">Metoda SqlStreamChars.Write (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="26093-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="26093-103">W przypadku przesłonięcia w klasie pochodnej, zapisuje sekwencji znaków do bieżącego strumienia i przesuwa bieżącą pozycję w tym strumieniu według liczby znaków zapisanych.</span><span class="sxs-lookup"><span data-stu-id="26093-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="26093-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="26093-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="26093-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="26093-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="26093-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="26093-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="26093-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="26093-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="26093-108">Tablicy znaków do zapisania.</span><span class="sxs-lookup"><span data-stu-id="26093-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="26093-109">Przesunięcie względem źródła.</span><span class="sxs-lookup"><span data-stu-id="26093-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="26093-110">Liczba znaków, które mają być zapisywane do strumienia bieżącego.</span><span class="sxs-lookup"><span data-stu-id="26093-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="26093-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26093-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="26093-112">`SqlStreamChars.Write` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="26093-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="26093-113">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="26093-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="26093-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26093-114">Requirements</span></span>

<span data-ttu-id="26093-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="26093-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="26093-116">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="26093-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="26093-117">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="26093-117">**.NET Framework versions:** Available since 2.0.</span></span>