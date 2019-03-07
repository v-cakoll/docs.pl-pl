---
title: Metoda ICorDebugSymbolProvider::GetAssemblyImageMetadata
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cb255330937b00a987ee0d07f0332d04fe1746d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489985"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="63dc0-102">Metoda ICorDebugSymbolProvider::GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="63dc0-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="63dc0-103">Zwraca metadane z zestawu scalonych.</span><span class="sxs-lookup"><span data-stu-id="63dc0-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63dc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63dc0-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63dc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63dc0-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="63dc0-106">[out] Wskaźnik na adres [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiektu, który zawiera informacje o rozmiarze i adres metadanych zestawu scalonych.</span><span class="sxs-lookup"><span data-stu-id="63dc0-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63dc0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63dc0-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63dc0-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="63dc0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63dc0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63dc0-109">Requirements</span></span>  
 <span data-ttu-id="63dc0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63dc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63dc0-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63dc0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63dc0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63dc0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63dc0-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63dc0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63dc0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63dc0-114">See also</span></span>
- [<span data-ttu-id="63dc0-115">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="63dc0-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="63dc0-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="63dc0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
