---
title: "ICorDebugMergedAssemblyRecord::GetPublicKey — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a47eb051cd9922b8640b8b612ff0ac5882b6a8ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="ad3e2-102">ICorDebugMergedAssemblyRecord::GetPublicKey — metoda</span><span class="sxs-lookup"><span data-stu-id="ad3e2-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="ad3e2-103">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad3e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad3e2-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad3e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad3e2-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="ad3e2-106">[in] Maksymalna liczba bajtów w `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="ad3e2-107">[out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="ad3e2-108">[out] Wskaźnik do tablicy typu byte, który zawiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad3e2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad3e2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad3e2-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad3e2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad3e2-111">Requirements</span></span>  
 <span data-ttu-id="ad3e2-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad3e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad3e2-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad3e2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad3e2-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad3e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad3e2-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad3e2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3e2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad3e2-116">See Also</span></span>  
 [<span data-ttu-id="ad3e2-117">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad3e2-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="ad3e2-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ad3e2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
