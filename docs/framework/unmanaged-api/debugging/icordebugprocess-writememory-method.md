---
title: ICorDebugProcess::WriteMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da4c282c7f969a406a657d1e30dd6120a32b4e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="9ed00-102">ICorDebugProcess::WriteMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ed00-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="9ed00-103">Zapisuje dane do to obszar pamięci w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="9ed00-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ed00-104">Syntax</span></span>  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ed00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ed00-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9ed00-106">[in] A `CORDB_ADDRESS` wartość, która jest adresem podstawowym obszaru pamięci dane są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="9ed00-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="9ed00-107">Przed wystąpieniem transferu danych, system sprawdza, czy obszar pamięci o określonym rozmiarze, rozpoczynając od adres podstawowy jest dostępny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="9ed00-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="9ed00-108">Jeśli nie jest dostępny, metoda kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9ed00-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="9ed00-109">[in] Liczba bajtów do zapisania w obszarze pamięci.</span><span class="sxs-lookup"><span data-stu-id="9ed00-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9ed00-110">[in] Buforu, który zawiera dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="9ed00-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="9ed00-111">[out] Wskaźnik do zmiennej, która odbiera liczba bajtów zapisanych do obszaru pamięci w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="9ed00-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="9ed00-112">Jeśli `written` ma wartość NULL, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="9ed00-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ed00-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ed00-113">Remarks</span></span>  
 <span data-ttu-id="9ed00-114">Dane są automatycznie zapisywane za wszystkie punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="9ed00-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="9ed00-115">W programie .NET Framework w wersji 2.0 natywnego debugery nie należy używać tej metody można wstawić punktów przerwania do strumienia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9ed00-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="9ed00-116">Użyj [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="9ed00-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="9ed00-117">`WriteMemory` Metoda powinna być używana tylko poza kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9ed00-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="9ed00-118">Ta metoda może uszkodzić środowiska uruchomieniowego, użycie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="9ed00-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed00-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ed00-119">Requirements</span></span>  
 <span data-ttu-id="9ed00-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed00-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed00-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ed00-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ed00-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed00-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed00-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed00-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
