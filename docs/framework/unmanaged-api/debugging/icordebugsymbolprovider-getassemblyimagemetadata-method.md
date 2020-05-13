---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: d118f0c984663e0844783ff52859698dd5335058
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376145"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="4de5f-102">ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda</span><span class="sxs-lookup"><span data-stu-id="4de5f-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="4de5f-103">Zwraca metadane z scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4de5f-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4de5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4de5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4de5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4de5f-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="4de5f-106">określoną Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , który zawiera informacje o rozmiarze i adresie metadanych scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4de5f-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4de5f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4de5f-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4de5f-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4de5f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4de5f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4de5f-109">Requirements</span></span>  
 <span data-ttu-id="4de5f-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4de5f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4de5f-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4de5f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4de5f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4de5f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4de5f-113">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4de5f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de5f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4de5f-114">See also</span></span>

- [<span data-ttu-id="4de5f-115">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="4de5f-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4de5f-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4de5f-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
