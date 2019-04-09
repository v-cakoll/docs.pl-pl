---
title: Metoda ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b20d78abbfa1db43047872a596289028833de37d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098991"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="54957-102">Metoda ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="54957-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="54957-103">Zwraca metodę uruchamiania względny adres wirtualny, metody i podany kod względny adres wirtualny nadrzędnej ramki.</span><span class="sxs-lookup"><span data-stu-id="54957-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54957-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54957-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54957-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54957-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="54957-106">[in] Względny adres wirtualny kodu.</span><span class="sxs-lookup"><span data-stu-id="54957-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="54957-107">[out] Wskaźnik do metody uruchamiania względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="54957-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="54957-108">[out] Wskaźnik do ramki uruchamianie względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="54957-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54957-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54957-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54957-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="54957-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54957-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54957-111">Requirements</span></span>  
 <span data-ttu-id="54957-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54957-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54957-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54957-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54957-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54957-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="54957-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="54957-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54957-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54957-116">See also</span></span>

- [<span data-ttu-id="54957-117">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="54957-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="54957-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="54957-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
