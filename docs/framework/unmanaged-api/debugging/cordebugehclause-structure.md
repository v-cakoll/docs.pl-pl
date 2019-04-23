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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839e698c8921f916fad174bae4f4cc8bb4d02994
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157329"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="9bca6-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="9bca6-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="9bca6-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="9bca6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9bca6-104">Reprezentuje wyjątek obsługi klauzuli (EH) dla danego kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="9bca6-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bca6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bca6-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9bca6-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9bca6-106">Members</span></span>  
  
|<span data-ttu-id="9bca6-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9bca6-107">Member</span></span>|<span data-ttu-id="9bca6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9bca6-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="9bca6-109">Pole bitowe, który opisuje informacje o wyjątku w klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="9bca6-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="9bca6-110">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="9bca6-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="9bca6-111">Przesunięcie, w bajtach, z `try` bloku od początku treści metody.</span><span class="sxs-lookup"><span data-stu-id="9bca6-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="9bca6-112">Długość w bajtach z `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="9bca6-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="9bca6-113">Lokalizacja programu obsługi dla tego `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="9bca6-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="9bca6-114">Rozmiar kod obsługi w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9bca6-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="9bca6-115">Token metadanych w przypadku obsługi na podstawie typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9bca6-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="9bca6-116">Przesunięcie w bajtach od początku treści metody obsługi wyjątków na podstawie filtru.</span><span class="sxs-lookup"><span data-stu-id="9bca6-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bca6-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bca6-117">Remarks</span></span>  
 <span data-ttu-id="9bca6-118">Tablica `CoreDebugEHClause` wartości jest zwracana przez [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9bca6-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="9bca6-119">Informacje o klauzuli EH jest definiowany przez specyfikację interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9bca6-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="9bca6-120">Aby uzyskać więcej informacji, zobacz [Standard ECMA-355: Common Language Infrastructure (CLI), wersja 6](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="9bca6-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="9bca6-121">`flags` Pole może zawierać następujących flag.</span><span class="sxs-lookup"><span data-stu-id="9bca6-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="9bca6-122">Należy pamiętać, że nie są zdefiniowane w CorDebug.idl lub CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="9bca6-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="9bca6-123">Flaga</span><span class="sxs-lookup"><span data-stu-id="9bca6-123">Flag</span></span>|<span data-ttu-id="9bca6-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="9bca6-124">Value</span></span>|<span data-ttu-id="9bca6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9bca6-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="9bca6-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="9bca6-126">0x00000000</span></span>|<span data-ttu-id="9bca6-127">Klauzula typizowanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9bca6-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="9bca6-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="9bca6-128">0x00000001</span></span>|<span data-ttu-id="9bca6-129">Wyjątek filtr i obsługi klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9bca6-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="9bca6-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="9bca6-130">0x00000002</span></span>|<span data-ttu-id="9bca6-131">A `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9bca6-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="9bca6-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="9bca6-132">0x00000004</span></span>|<span data-ttu-id="9bca6-133">Klauzuli fault ( `finally` klauzula, która jest wywoływana tylko wtedy, gdy zostanie zgłoszony wyjątek).</span><span class="sxs-lookup"><span data-stu-id="9bca6-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bca6-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bca6-134">Requirements</span></span>  
 <span data-ttu-id="9bca6-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bca6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bca6-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bca6-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bca6-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bca6-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bca6-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bca6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bca6-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bca6-139">See also</span></span>

- [<span data-ttu-id="9bca6-140">GetEHClauses, metoda</span><span class="sxs-lookup"><span data-stu-id="9bca6-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="9bca6-141">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="9bca6-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
