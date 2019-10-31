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
ms.openlocfilehash: 87316b20c5835d9b887355a1f9374fa5f2156e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122174"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="08fc3-102">ICorDebugDataTarget::ReadVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="08fc3-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="08fc3-103">Pobiera blok ciągłej pamięci zaczynający się od określonego adresu i zwraca go w dostarczonym buforze.</span><span class="sxs-lookup"><span data-stu-id="08fc3-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08fc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08fc3-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08fc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08fc3-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="08fc3-106">podczas Adres początkowy żądanej pamięci.</span><span class="sxs-lookup"><span data-stu-id="08fc3-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="08fc3-107">określoną Bufor, w którym będzie przechowywana pamięć.</span><span class="sxs-lookup"><span data-stu-id="08fc3-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="08fc3-108">podczas Liczba bajtów pobieranych z adresu docelowego.</span><span class="sxs-lookup"><span data-stu-id="08fc3-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="08fc3-109">określoną Liczba bajtów faktycznie odczytywanych z adresu docelowego.</span><span class="sxs-lookup"><span data-stu-id="08fc3-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="08fc3-110">Może to być mniejsze niż `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="08fc3-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08fc3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08fc3-111">Remarks</span></span>  
 <span data-ttu-id="08fc3-112">W przypadku odczytywania pierwszego bajtu (na określonym adresie początkowym) wywołanie powinno zwrócić sukces (w celu zapewnienia obsługi wydajnego odczytu struktur danych z unikatową długością, na przykład w przypadku ciągów zakończonych znakiem null).</span><span class="sxs-lookup"><span data-stu-id="08fc3-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08fc3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08fc3-113">Requirements</span></span>  
 <span data-ttu-id="08fc3-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08fc3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08fc3-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08fc3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08fc3-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08fc3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08fc3-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08fc3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fc3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08fc3-118">See also</span></span>

- [<span data-ttu-id="08fc3-119">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="08fc3-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="08fc3-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="08fc3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="08fc3-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="08fc3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
