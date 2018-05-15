---
title: ICorDebugDataTarget::ReadVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d9e619e4176633074242521133d42f191f140ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="86fc9-102">ICorDebugDataTarget::ReadVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="86fc9-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="86fc9-103">Pobiera blok pamięci ciągłej, zaczynając od określonego adresu i zwraca go do dostarczonego buforu.</span><span class="sxs-lookup"><span data-stu-id="86fc9-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86fc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86fc9-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86fc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86fc9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="86fc9-106">[in] Adres początkowy żądaną ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="86fc9-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="86fc9-107">[out] Bufor, w którym będzie przechowywany pamięci.</span><span class="sxs-lookup"><span data-stu-id="86fc9-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="86fc9-108">[in] Liczba bajtów do pobrania z adresu docelowego.</span><span class="sxs-lookup"><span data-stu-id="86fc9-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="86fc9-109">[out] Liczba bajtów odczytanych w rzeczywistości z adresu docelowego.</span><span class="sxs-lookup"><span data-stu-id="86fc9-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="86fc9-110">Może to być krótsza niż `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="86fc9-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86fc9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86fc9-111">Remarks</span></span>  
 <span data-ttu-id="86fc9-112">Jeśli pierwszy bajt (pod adresem określonym start) mogą być odczytywane; wywołanie powinien zwrócić Powodzenie (do obsługi wydajne odczytu struktur danych z samoopisujące długość, takie jak ciągi zakończone wartością null).</span><span class="sxs-lookup"><span data-stu-id="86fc9-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86fc9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86fc9-113">Requirements</span></span>  
 <span data-ttu-id="86fc9-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86fc9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86fc9-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86fc9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86fc9-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86fc9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86fc9-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86fc9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86fc9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86fc9-118">See Also</span></span>  
 [<span data-ttu-id="86fc9-119">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="86fc9-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="86fc9-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="86fc9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="86fc9-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="86fc9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
