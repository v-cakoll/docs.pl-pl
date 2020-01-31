---
title: Metoda ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: bada60295c3a9b3a702aa674e06f8f5cf6ac0a24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788829"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="8bed3-102">Metoda ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="8bed3-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="8bed3-103">Zwraca dostawcę symboli dla modułu z adresu podstawowego tego modułu.</span><span class="sxs-lookup"><span data-stu-id="8bed3-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bed3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bed3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bed3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bed3-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="8bed3-106">podczas Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="8bed3-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="8bed3-107">określoną Wskaźnik do adresu obiektu [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8bed3-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bed3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bed3-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bed3-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8bed3-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bed3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bed3-110">Requirements</span></span>  
 <span data-ttu-id="8bed3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bed3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bed3-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8bed3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bed3-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8bed3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bed3-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bed3-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bed3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bed3-115">See also</span></span>

- [<span data-ttu-id="8bed3-116">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bed3-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="8bed3-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8bed3-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
