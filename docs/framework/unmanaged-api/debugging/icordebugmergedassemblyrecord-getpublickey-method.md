---
title: ICorDebugMergedAssemblyRecord::GetPublicKey Method
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107279"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="b8eea-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span><span class="sxs-lookup"><span data-stu-id="b8eea-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="b8eea-103">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8eea-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8eea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8eea-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8eea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8eea-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="b8eea-106">[in] Maksymalna liczba bajtów w `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8eea-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b8eea-107">[out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8eea-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="b8eea-108">[out] Wskaźnik do tablicy typu byte, który zawiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8eea-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8eea-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8eea-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8eea-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b8eea-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8eea-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8eea-111">Requirements</span></span>  
 <span data-ttu-id="b8eea-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8eea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8eea-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8eea-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8eea-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8eea-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b8eea-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b8eea-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8eea-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8eea-116">See also</span></span>

- [<span data-ttu-id="b8eea-117">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8eea-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="b8eea-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b8eea-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
