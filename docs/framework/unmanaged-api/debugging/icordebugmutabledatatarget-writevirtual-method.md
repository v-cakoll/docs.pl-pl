---
title: "ICorDebugMutableDataTarget::WriteVirtual — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9541a324c448312f50858ea0b1b284585d223edf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="23b46-102">ICorDebugMutableDataTarget::WriteVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="23b46-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="23b46-103">Zapisuje pamięci do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="23b46-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23b46-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23b46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23b46-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="23b46-106">[in] Adres, pod którym można zapisać zawartości `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="23b46-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="23b46-107">[in] Wskaźnik do tablicy typu byte, który zawiera bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="23b46-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="23b46-108">[in] Liczba bajtów w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="23b46-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23b46-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23b46-109">Return Value</span></span>  
 <span data-ttu-id="23b46-110">`S_OK`na powodzenie lub innych `HRESULT` w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="23b46-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23b46-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23b46-111">Remarks</span></span>  
 <span data-ttu-id="23b46-112">Jeśli nie można zapisać wszystkich bajtów, wywołanie metody kończy się niepowodzeniem bez zmieniania żadnych bajtów w docelowej przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="23b46-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="23b46-113">(W przeciwnym razie element docelowy będzie można w stanie niespójnym, która sprawia, że dalsze debugowania zawodne.)</span><span class="sxs-lookup"><span data-stu-id="23b46-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b46-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23b46-114">Requirements</span></span>  
 <span data-ttu-id="23b46-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23b46-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b46-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23b46-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23b46-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23b46-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23b46-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b46-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b46-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23b46-119">See Also</span></span>  
 [<span data-ttu-id="23b46-120">Interfejs ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="23b46-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="23b46-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="23b46-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
