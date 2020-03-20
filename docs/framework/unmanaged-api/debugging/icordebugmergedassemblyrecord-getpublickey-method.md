---
title: ICorDebugMergedAssemblyRecord::Metoda GetPublicKey
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 632e990899346493d5a7df08d293e25b83ed7ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178742"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="85d0d-102">ICorDebugMergedAssemblyRecord::Metoda GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="85d0d-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="85d0d-103">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="85d0d-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85d0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85d0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85d0d-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="85d0d-106">[w] Maksymalna liczba bajtów `pbPublicKey` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="85d0d-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="85d0d-107">[na zewnątrz] Wskaźnik do rzeczywistej liczby bajtów `pbPublicKey` zapisanych w tablicy.</span><span class="sxs-lookup"><span data-stu-id="85d0d-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="85d0d-108">[na zewnątrz] Wskaźnik do tablicy bajtów, która zawiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="85d0d-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85d0d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85d0d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85d0d-110">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="85d0d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d0d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85d0d-111">Requirements</span></span>  
 <span data-ttu-id="85d0d-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d0d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d0d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85d0d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85d0d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85d0d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85d0d-115">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d0d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d0d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85d0d-116">See also</span></span>

- [<span data-ttu-id="85d0d-117">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="85d0d-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="85d0d-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="85d0d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
