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
ms.openlocfilehash: a889d6ba00c4a0eb96a9923a7dbe52f3b93aaba5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795964"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="8ae77-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="8ae77-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="8ae77-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="8ae77-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8ae77-104">Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="8ae77-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae77-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ae77-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8ae77-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8ae77-106">Members</span></span>  
  
|<span data-ttu-id="8ae77-107">Członek</span><span class="sxs-lookup"><span data-stu-id="8ae77-107">Member</span></span>|<span data-ttu-id="8ae77-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae77-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="8ae77-109">Pole bitowe opisujące informacje o wyjątku w klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="8ae77-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="8ae77-110">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="8ae77-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="8ae77-111">Przesunięcie, w bajtach, `try` bloku od początku treści metody.</span><span class="sxs-lookup"><span data-stu-id="8ae77-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="8ae77-112">Długość (w bajtach) `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="8ae77-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="8ae77-113">Lokalizacja programu obsługi dla tego `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="8ae77-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="8ae77-114">Rozmiar kodu programu obsługi w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8ae77-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="8ae77-115">Token metadanych dla obsługi wyjątków opartych na typie.</span><span class="sxs-lookup"><span data-stu-id="8ae77-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="8ae77-116">Przesunięcie, w bajtach, od początku treści metody dla procedury obsługi wyjątków opartej na filtrze.</span><span class="sxs-lookup"><span data-stu-id="8ae77-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ae77-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ae77-117">Remarks</span></span>  
 <span data-ttu-id="8ae77-118">Tablica `CoreDebugEHClause` wartości jest zwracana przez metodę [GetEHClauses](icordebugilcode-getehclauses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8ae77-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="8ae77-119">Informacje o klauzuli EH są definiowane przez specyfikację interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8ae77-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="8ae77-120">Aby uzyskać więcej informacji, zobacz [Standard ECMA-355: Common Language Infrastructure (CLI), Wydanie szóste](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="8ae77-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="8ae77-121">`flags` Pole może zawierać następujące flagi.</span><span class="sxs-lookup"><span data-stu-id="8ae77-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="8ae77-122">Należy zauważyć, że nie są one zdefiniowane w CorDebug. idl lub CorDebug. h.</span><span class="sxs-lookup"><span data-stu-id="8ae77-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="8ae77-123">Flaga</span><span class="sxs-lookup"><span data-stu-id="8ae77-123">Flag</span></span>|<span data-ttu-id="8ae77-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="8ae77-124">Value</span></span>|<span data-ttu-id="8ae77-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8ae77-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="8ae77-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="8ae77-126">0x00000000</span></span>|<span data-ttu-id="8ae77-127">Klauzula wyjątku o określonym typie.</span><span class="sxs-lookup"><span data-stu-id="8ae77-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="8ae77-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="8ae77-128">0x00000001</span></span>|<span data-ttu-id="8ae77-129">Filtr wyjątku i klauzula obsługi.</span><span class="sxs-lookup"><span data-stu-id="8ae77-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="8ae77-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="8ae77-130">0x00000002</span></span>|<span data-ttu-id="8ae77-131">`finally` Klauzula.</span><span class="sxs-lookup"><span data-stu-id="8ae77-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="8ae77-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="8ae77-132">0x00000004</span></span>|<span data-ttu-id="8ae77-133">Klauzula błędu ( `finally` klauzula, która jest wywoływana tylko w przypadku zgłoszenia wyjątku).</span><span class="sxs-lookup"><span data-stu-id="8ae77-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ae77-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ae77-134">Requirements</span></span>  
 <span data-ttu-id="8ae77-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ae77-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ae77-136">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ae77-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ae77-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8ae77-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ae77-138">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ae77-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae77-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ae77-139">See also</span></span>

- [<span data-ttu-id="8ae77-140">GetEHClauses, metoda</span><span class="sxs-lookup"><span data-stu-id="8ae77-140">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="8ae77-141">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="8ae77-141">Debugging Structures</span></span>](debugging-structures.md)
