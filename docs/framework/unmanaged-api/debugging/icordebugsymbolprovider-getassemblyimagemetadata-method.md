---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: fb08df3b594e0c34dfe4ca791983b0c111239b23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138905"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="62607-102">ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda</span><span class="sxs-lookup"><span data-stu-id="62607-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="62607-103">Zwraca metadane z scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="62607-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62607-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62607-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62607-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62607-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="62607-106">określoną Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) , który zawiera informacje o rozmiarze i adresie metadanych scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="62607-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62607-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62607-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62607-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="62607-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62607-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62607-109">Requirements</span></span>  
 <span data-ttu-id="62607-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62607-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62607-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62607-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62607-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="62607-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62607-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62607-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62607-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62607-114">See also</span></span>

- [<span data-ttu-id="62607-115">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="62607-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="62607-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="62607-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
