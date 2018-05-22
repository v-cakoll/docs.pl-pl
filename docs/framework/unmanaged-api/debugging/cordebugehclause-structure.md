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
ms.openlocfilehash: 40820a805310786eeb0effd7c5284c1a70a6e70b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="54799-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="54799-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="54799-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="54799-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="54799-104">Reprezentuje wyjątek klauzuli (EH) dla danej fragment kodu w języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="54799-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54799-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="54799-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="54799-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54799-106">Members</span></span>  
  
|<span data-ttu-id="54799-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="54799-107">Member</span></span>|<span data-ttu-id="54799-108">Opis</span><span class="sxs-lookup"><span data-stu-id="54799-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="54799-109">Pole bitowe, który opisuje informacje o wyjątku w klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="54799-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="54799-110">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="54799-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="54799-111">Przesunięcie, w bajtach z `try` bloku od początku treści metody.</span><span class="sxs-lookup"><span data-stu-id="54799-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="54799-112">Długość w bajtach z `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="54799-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="54799-113">Lokalizacja programu obsługi dla tego `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="54799-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="54799-114">Rozmiar kod obsługi w bajtach.</span><span class="sxs-lookup"><span data-stu-id="54799-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="54799-115">Token metadanych dla obsługi wyjątków na podstawie typu.</span><span class="sxs-lookup"><span data-stu-id="54799-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="54799-116">Przesunięcie w bajtach, od początku treści metody obsługi na podstawie filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="54799-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54799-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54799-117">Remarks</span></span>  
 <span data-ttu-id="54799-118">Tablica `CoreDebugEHClause` wartości zwracane przez [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="54799-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="54799-119">Informacje klauzuli EH jest zdefiniowany w specyfikacji interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="54799-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="54799-120">Aby uzyskać więcej informacji, zobacz [standardowe ECMA-355: infrastruktury języka wspólnego (CLI), w wersji 6](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="54799-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="54799-121">`flags` Pole może zawierać następujące flagi.</span><span class="sxs-lookup"><span data-stu-id="54799-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="54799-122">Należy pamiętać, że nie są zdefiniowane w CorDebug.idl lub CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="54799-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="54799-123">Flaga</span><span class="sxs-lookup"><span data-stu-id="54799-123">Flag</span></span>|<span data-ttu-id="54799-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="54799-124">Value</span></span>|<span data-ttu-id="54799-125">Opis</span><span class="sxs-lookup"><span data-stu-id="54799-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="54799-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="54799-126">0x00000000</span></span>|<span data-ttu-id="54799-127">Klauzula typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="54799-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="54799-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="54799-128">0x00000001</span></span>|<span data-ttu-id="54799-129">Wyjątek filtru i obsługi klauzuli.</span><span class="sxs-lookup"><span data-stu-id="54799-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="54799-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="54799-130">0x00000002</span></span>|<span data-ttu-id="54799-131">A `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="54799-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="54799-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="54799-132">0x00000004</span></span>|<span data-ttu-id="54799-133">Klauzula usterek ( `finally` klauzuli, która jest wywoływana tylko wtedy, gdy jest zgłaszany wyjątek).</span><span class="sxs-lookup"><span data-stu-id="54799-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54799-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54799-134">Requirements</span></span>  
 <span data-ttu-id="54799-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54799-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54799-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54799-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54799-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54799-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54799-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54799-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54799-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54799-139">See Also</span></span>  
 [<span data-ttu-id="54799-140">GetEHClauses, metoda</span><span class="sxs-lookup"><span data-stu-id="54799-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [<span data-ttu-id="54799-141">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="54799-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
