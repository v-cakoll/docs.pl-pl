---
title: Struktura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: f35e979a5107064d2987a385a989075ef71283ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098861"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="0931c-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="0931c-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="0931c-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="0931c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0931c-104">Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="0931c-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0931c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0931c-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="0931c-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0931c-106">Members</span></span>  
  
|<span data-ttu-id="0931c-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0931c-107">Member</span></span>|<span data-ttu-id="0931c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0931c-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="0931c-109">Pole bitowe opisujące informacje o wyjątku w klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="0931c-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="0931c-110">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="0931c-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="0931c-111">Przesunięcie, w bajtach, bloku `try` od początku treści metody.</span><span class="sxs-lookup"><span data-stu-id="0931c-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="0931c-112">Długość (w bajtach) bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="0931c-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="0931c-113">Lokalizacja programu obsługi dla tego bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="0931c-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="0931c-114">Rozmiar kodu programu obsługi w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0931c-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="0931c-115">Token metadanych dla obsługi wyjątków opartych na typie.</span><span class="sxs-lookup"><span data-stu-id="0931c-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="0931c-116">Przesunięcie, w bajtach, od początku treści metody dla procedury obsługi wyjątków opartej na filtrze.</span><span class="sxs-lookup"><span data-stu-id="0931c-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0931c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0931c-117">Remarks</span></span>  
 <span data-ttu-id="0931c-118">Tablica wartości `CoreDebugEHClause` jest zwracana przez metodę [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0931c-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="0931c-119">Informacje o klauzuli EH są definiowane przez specyfikację interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0931c-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="0931c-120">Aby uzyskać więcej informacji, zobacz [Standard ECMA-355: Common Language Infrastructure (CLI), Wydanie szóste](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="0931c-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="0931c-121">Pole `flags` może zawierać następujące flagi.</span><span class="sxs-lookup"><span data-stu-id="0931c-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="0931c-122">Należy zauważyć, że nie są one zdefiniowane w CorDebug. idl lub CorDebug. h.</span><span class="sxs-lookup"><span data-stu-id="0931c-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="0931c-123">znacznik</span><span class="sxs-lookup"><span data-stu-id="0931c-123">Flag</span></span>|<span data-ttu-id="0931c-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="0931c-124">Value</span></span>|<span data-ttu-id="0931c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0931c-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="0931c-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="0931c-126">0x00000000</span></span>|<span data-ttu-id="0931c-127">Klauzula wyjątku o określonym typie.</span><span class="sxs-lookup"><span data-stu-id="0931c-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="0931c-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="0931c-128">0x00000001</span></span>|<span data-ttu-id="0931c-129">Filtr wyjątku i klauzula obsługi.</span><span class="sxs-lookup"><span data-stu-id="0931c-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="0931c-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="0931c-130">0x00000002</span></span>|<span data-ttu-id="0931c-131">Klauzula `finally`.</span><span class="sxs-lookup"><span data-stu-id="0931c-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="0931c-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="0931c-132">0x00000004</span></span>|<span data-ttu-id="0931c-133">Klauzula błędu (klauzula `finally`, która jest wywoływana tylko w przypadku zgłoszenia wyjątku).</span><span class="sxs-lookup"><span data-stu-id="0931c-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0931c-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0931c-134">Requirements</span></span>  
 <span data-ttu-id="0931c-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0931c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0931c-136">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0931c-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0931c-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0931c-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0931c-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0931c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0931c-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0931c-139">See also</span></span>

- [<span data-ttu-id="0931c-140">GetEHClauses, metoda</span><span class="sxs-lookup"><span data-stu-id="0931c-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="0931c-141">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="0931c-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
