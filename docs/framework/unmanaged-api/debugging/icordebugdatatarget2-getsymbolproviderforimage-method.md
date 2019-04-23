---
title: Metoda ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cda49084c9453f79727f7f57ef152577cb4d7c5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171967"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="d1c9e-102">Metoda ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="d1c9e-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="d1c9e-103">Zwraca adres bazowy modułu, dostawca symboli dla modułu.</span><span class="sxs-lookup"><span data-stu-id="d1c9e-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1c9e-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1c9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1c9e-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="d1c9e-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="d1c9e-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="d1c9e-107">[out] Wskaźnik na adres [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d1c9e-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1c9e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1c9e-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1c9e-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d1c9e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c9e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1c9e-110">Requirements</span></span>  
 <span data-ttu-id="d1c9e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c9e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c9e-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1c9e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1c9e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1c9e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1c9e-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c9e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c9e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1c9e-115">See also</span></span>

- [<span data-ttu-id="d1c9e-116">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1c9e-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="d1c9e-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1c9e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
