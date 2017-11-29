---
title: "ICorDebugSymbolProvider::GetCodeRange — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c46fb62e5f1867e2b527404bd3d003ba884ebfbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="f8860-102">ICorDebugSymbolProvider::GetCodeRange — metoda</span><span class="sxs-lookup"><span data-stu-id="f8860-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="f8860-103">Pobiera adres początkowy — metoda i rozmiar podany wirtualny adres względny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="f8860-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8860-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8860-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8860-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8860-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="f8860-106">[in] Wirtualny adres względny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="f8860-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="f8860-107">[out] Wskaźnik do metody adres początkowy.</span><span class="sxs-lookup"><span data-stu-id="f8860-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="f8860-108">Wskaźnik do rozmiaru kodu — metoda (liczba bajtów kod metody).</span><span class="sxs-lookup"><span data-stu-id="f8860-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8860-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8860-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8860-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f8860-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8860-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8860-111">Requirements</span></span>  
 <span data-ttu-id="f8860-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8860-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8860-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8860-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8860-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8860-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8860-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8860-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8860-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8860-116">See Also</span></span>  
 [<span data-ttu-id="f8860-117">Interfejs ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="f8860-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="f8860-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="f8860-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
