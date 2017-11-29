---
title: "ICorDebugSymbolProvider2::GetFrameProps — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3892b8da3286132709792513f055d6ce75bd3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="3de24-102">ICorDebugSymbolProvider2::GetFrameProps — metoda</span><span class="sxs-lookup"><span data-stu-id="3de24-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="3de24-103">Zwraca metodę uruchamiania wirtualny adres względny metody i ramka nadrzędny podany wirtualny adres względny kodu.</span><span class="sxs-lookup"><span data-stu-id="3de24-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3de24-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3de24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3de24-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="3de24-106">[in] Kod wirtualnego adresu względnego.</span><span class="sxs-lookup"><span data-stu-id="3de24-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="3de24-107">[out] Wskaźnik do metody uruchamiania wirtualny adres względny.</span><span class="sxs-lookup"><span data-stu-id="3de24-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="3de24-108">[out] Wskaźnik do ramki względną wirtualny adres początkowy.</span><span class="sxs-lookup"><span data-stu-id="3de24-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3de24-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3de24-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3de24-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3de24-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de24-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3de24-111">Requirements</span></span>  
 <span data-ttu-id="3de24-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de24-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de24-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3de24-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3de24-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3de24-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3de24-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de24-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de24-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3de24-116">See Also</span></span>  
 [<span data-ttu-id="3de24-117">Interfejs ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="3de24-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="3de24-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="3de24-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
