---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48e5e9daf191cb2f4112dd2a957f29c0a7521398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="3c7e9-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata — metoda</span><span class="sxs-lookup"><span data-stu-id="3c7e9-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="3c7e9-103">Zwraca metadane z zestawu scalone.</span><span class="sxs-lookup"><span data-stu-id="3c7e9-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c7e9-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c7e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c7e9-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="3c7e9-106">[out] Wskaźnik do adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiekt, który zawiera informacje o rozmiar i adres metadanych zestawu scalone.</span><span class="sxs-lookup"><span data-stu-id="3c7e9-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c7e9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c7e9-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c7e9-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3c7e9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c7e9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c7e9-109">Requirements</span></span>  
 <span data-ttu-id="3c7e9-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c7e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c7e9-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c7e9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c7e9-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c7e9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c7e9-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c7e9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7e9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c7e9-114">See Also</span></span>  
 [<span data-ttu-id="3c7e9-115">Interfejs ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="3c7e9-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="3c7e9-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="3c7e9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
