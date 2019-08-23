---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad86c42d0f23de25fe0e5b9123a0dba3695d8d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964657"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="7d77e-102">ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda</span><span class="sxs-lookup"><span data-stu-id="7d77e-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="7d77e-103">Zwraca metadane z scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d77e-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d77e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d77e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d77e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d77e-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="7d77e-106">określoną Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) , który zawiera informacje o rozmiarze i adresie metadanych scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d77e-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d77e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d77e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d77e-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7d77e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d77e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d77e-109">Requirements</span></span>  
 <span data-ttu-id="7d77e-110">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d77e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d77e-111">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d77e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d77e-112">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d77e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d77e-113">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d77e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d77e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d77e-114">See also</span></span>

- [<span data-ttu-id="7d77e-115">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d77e-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7d77e-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7d77e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
