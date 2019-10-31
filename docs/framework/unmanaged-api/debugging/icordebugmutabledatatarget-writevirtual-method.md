---
title: 'ICorDebugMutableDataTarget:: WriteVirtual —, Metoda'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 5947caa8dfb97574bb4b3c5634d962df153211c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132678"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="50258-102">ICorDebugMutableDataTarget:: WriteVirtual —, Metoda</span><span class="sxs-lookup"><span data-stu-id="50258-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="50258-103">Zapisuje pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="50258-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50258-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50258-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50258-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50258-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="50258-106">podczas Adres, pod który należy napisać zawartość `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="50258-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="50258-107">podczas Wskaźnik do tablicy bajtów zawierającej bajty do zapisania.</span><span class="sxs-lookup"><span data-stu-id="50258-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="50258-108">podczas Liczba bajtów w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="50258-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50258-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50258-109">Return Value</span></span>  
 <span data-ttu-id="50258-110">`S_OK` po powodzeniu lub innych `HRESULT` w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="50258-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50258-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50258-111">Remarks</span></span>  
 <span data-ttu-id="50258-112">Jeśli nie można zapisać żadnych bajtów, wywołanie metody zakończy się niepowodzeniem bez zmiany jakichkolwiek bajtów w docelowej przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="50258-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="50258-113">(W przeciwnym razie element docelowy będzie w stanie niespójnym, co sprawia, że dalsze debugowanie jest niezawodne).</span><span class="sxs-lookup"><span data-stu-id="50258-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50258-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50258-114">Requirements</span></span>  
 <span data-ttu-id="50258-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50258-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50258-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50258-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50258-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="50258-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50258-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50258-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50258-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50258-119">See also</span></span>

- [<span data-ttu-id="50258-120">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="50258-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="50258-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="50258-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
