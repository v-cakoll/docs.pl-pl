---
title: ICorDebugSymbolProvider2::GetFrameProps — metoda
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419e7bae5998679fafac48ebfd5b0673e0e4bac5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419084"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="0b183-102">ICorDebugSymbolProvider2::GetFrameProps — metoda</span><span class="sxs-lookup"><span data-stu-id="0b183-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="0b183-103">Zwraca metodę uruchamiania wirtualny adres względny metody i ramka nadrzędny podany wirtualny adres względny kodu.</span><span class="sxs-lookup"><span data-stu-id="0b183-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b183-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b183-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b183-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b183-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="0b183-106">[in] Kod wirtualnego adresu względnego.</span><span class="sxs-lookup"><span data-stu-id="0b183-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="0b183-107">[out] Wskaźnik do metody uruchamiania wirtualny adres względny.</span><span class="sxs-lookup"><span data-stu-id="0b183-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="0b183-108">[out] Wskaźnik do ramki względną wirtualny adres początkowy.</span><span class="sxs-lookup"><span data-stu-id="0b183-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b183-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b183-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b183-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0b183-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b183-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b183-111">Requirements</span></span>  
 <span data-ttu-id="0b183-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b183-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b183-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b183-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b183-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b183-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b183-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b183-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b183-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b183-116">See Also</span></span>  
 [<span data-ttu-id="0b183-117">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b183-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="0b183-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0b183-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
