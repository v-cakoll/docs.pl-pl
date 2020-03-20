---
title: Metoda ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 500d36b414be686071990a6e1b40dd8759d02ae9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178932"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="1ef0a-102">Metoda ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="1ef0a-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="1ef0a-103">Zwraca dostawcę symbolu dla modułu z adresu podstawowego tego modułu.</span><span class="sxs-lookup"><span data-stu-id="1ef0a-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ef0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ef0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ef0a-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="1ef0a-106">[w] Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) reprezentująca adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="1ef0a-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="1ef0a-107">[na zewnątrz] Wskaźnik do adresu [obiektu ICorDebugSymbolProvider.](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="1ef0a-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef0a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ef0a-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ef0a-109">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1ef0a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef0a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ef0a-110">Requirements</span></span>  
 <span data-ttu-id="1ef0a-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef0a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef0a-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ef0a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ef0a-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef0a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef0a-114">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef0a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef0a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ef0a-115">See also</span></span>

- [<span data-ttu-id="1ef0a-116">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ef0a-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="1ef0a-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1ef0a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
