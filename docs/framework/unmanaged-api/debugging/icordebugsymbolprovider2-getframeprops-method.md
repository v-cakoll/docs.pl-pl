---
title: Metoda ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c02a2b31ecc588879b43668d56cd9978b62e49a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482486"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="06d96-102">Metoda ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="06d96-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="06d96-103">Zwraca metodę uruchamiania względny adres wirtualny, metody i podany kod względny adres wirtualny nadrzędnej ramki.</span><span class="sxs-lookup"><span data-stu-id="06d96-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06d96-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06d96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06d96-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="06d96-106">[in] Względny adres wirtualny kodu.</span><span class="sxs-lookup"><span data-stu-id="06d96-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="06d96-107">[out] Wskaźnik do metody uruchamiania względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="06d96-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="06d96-108">[out] Wskaźnik do ramki uruchamianie względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="06d96-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06d96-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06d96-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06d96-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="06d96-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d96-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06d96-111">Requirements</span></span>  
 <span data-ttu-id="06d96-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06d96-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d96-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06d96-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06d96-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06d96-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06d96-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d96-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d96-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06d96-116">See also</span></span>
- [<span data-ttu-id="06d96-117">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="06d96-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="06d96-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="06d96-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
