---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ddb891091988a21013ee71272d489e7fd1f1283
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="13e5b-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="13e5b-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="13e5b-103">Zwraca adres podstawowy modułu i rozmiaru z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="13e5b-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13e5b-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13e5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13e5b-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="13e5b-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="13e5b-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="13e5b-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="13e5b-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="13e5b-108">Wskaźnik rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="13e5b-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13e5b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13e5b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13e5b-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="13e5b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e5b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13e5b-111">Requirements</span></span>  
 <span data-ttu-id="13e5b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e5b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e5b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13e5b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13e5b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13e5b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13e5b-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e5b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e5b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13e5b-116">See Also</span></span>  
 [<span data-ttu-id="13e5b-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="13e5b-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="13e5b-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="13e5b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
