---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfe25a90fb2084c1f58eff5b42e24b15decb0163
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="33a90-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="33a90-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="33a90-103">Zwraca adres podstawowy modułu i rozmiaru z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="33a90-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33a90-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33a90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33a90-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="33a90-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="33a90-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="33a90-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="33a90-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="33a90-108">Wskaźnik rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="33a90-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33a90-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33a90-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33a90-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="33a90-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a90-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33a90-111">Requirements</span></span>  
 <span data-ttu-id="33a90-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a90-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33a90-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33a90-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33a90-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33a90-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a90-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a90-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33a90-116">See Also</span></span>  
 [<span data-ttu-id="33a90-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="33a90-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="33a90-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="33a90-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
