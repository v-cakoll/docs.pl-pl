---
title: ICorDebugMutableDataTarget::WriteVirtual Method
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927377"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="2acc8-102">ICorDebugMutableDataTarget::WriteVirtual Method</span><span class="sxs-lookup"><span data-stu-id="2acc8-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="2acc8-103">Zapisuje w pamięci do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2acc8-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2acc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2acc8-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2acc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2acc8-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2acc8-106">[in] Adres, w którym należy zapisać zawartość `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2acc8-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="2acc8-107">[in] Wskaźnik do tablicy typu byte, zawierająca bajty do zapisania.</span><span class="sxs-lookup"><span data-stu-id="2acc8-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="2acc8-108">[in] Liczba bajtów w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2acc8-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2acc8-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2acc8-109">Return Value</span></span>  
 <span data-ttu-id="2acc8-110">`S_OK` na powodzenie lub innych `HRESULT` w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="2acc8-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2acc8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2acc8-111">Remarks</span></span>  
 <span data-ttu-id="2acc8-112">Nie można zapisać wszystkich bajtów, wywołanie metody nie powiedzie się bez zmieniania żadnych bajty w przestrzeni adresowej docelowego.</span><span class="sxs-lookup"><span data-stu-id="2acc8-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="2acc8-113">(W przeciwnym razie element docelowy będzie można w niespójnym stanie, który sprawia, że dodatkowe debugowanie zawodne.)</span><span class="sxs-lookup"><span data-stu-id="2acc8-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2acc8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2acc8-114">Requirements</span></span>  
 <span data-ttu-id="2acc8-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2acc8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2acc8-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2acc8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2acc8-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2acc8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2acc8-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2acc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2acc8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2acc8-119">See also</span></span>

- [<span data-ttu-id="2acc8-120">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="2acc8-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="2acc8-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2acc8-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
