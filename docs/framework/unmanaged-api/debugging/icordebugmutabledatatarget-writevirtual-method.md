---
title: ICorDebugMutableDataTarget::WriteVirtual — metoda
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="12296-102">ICorDebugMutableDataTarget::WriteVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="12296-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="12296-103">Zapisuje pamięci do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="12296-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12296-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12296-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12296-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12296-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="12296-106">[in] Adres, pod którym można zapisać zawartości `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="12296-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="12296-107">[in] Wskaźnik do tablicy typu byte, który zawiera bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="12296-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="12296-108">[in] Liczba bajtów w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="12296-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12296-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="12296-109">Return Value</span></span>  
 <span data-ttu-id="12296-110">`S_OK` na powodzenie lub innych `HRESULT` w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="12296-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12296-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12296-111">Remarks</span></span>  
 <span data-ttu-id="12296-112">Jeśli nie można zapisać wszystkich bajtów, wywołanie metody kończy się niepowodzeniem bez zmieniania żadnych bajtów w docelowej przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="12296-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="12296-113">(W przeciwnym razie element docelowy będzie można w stanie niespójnym, która sprawia, że dalsze debugowania zawodne.)</span><span class="sxs-lookup"><span data-stu-id="12296-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12296-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12296-114">Requirements</span></span>  
 <span data-ttu-id="12296-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12296-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12296-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12296-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12296-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12296-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12296-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12296-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12296-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12296-119">See Also</span></span>  
 [<span data-ttu-id="12296-120">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="12296-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="12296-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="12296-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
