---
title: ICorDebugSymbolProvider::GetCodeRange Method
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392f526df53474dd2926e631e24ec5449bd1b199
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498474"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="8ca97-102">ICorDebugSymbolProvider::GetCodeRange Method</span><span class="sxs-lookup"><span data-stu-id="8ca97-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="8ca97-103">Pobiera adres początkowy metody i biorąc względnych adresów wirtualnych (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="8ca97-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ca97-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ca97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ca97-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="8ca97-106">[in] Wirtualny adres względny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="8ca97-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="8ca97-107">[out] Wskaźnik do adres początkowy metody.</span><span class="sxs-lookup"><span data-stu-id="8ca97-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="8ca97-108">Wskaźnik do rozmiaru kodu — metoda (liczba bajtów kodu metody).</span><span class="sxs-lookup"><span data-stu-id="8ca97-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca97-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ca97-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ca97-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8ca97-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca97-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ca97-111">Requirements</span></span>  
 <span data-ttu-id="8ca97-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca97-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca97-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ca97-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ca97-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ca97-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ca97-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca97-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca97-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ca97-116">See also</span></span>
- [<span data-ttu-id="8ca97-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ca97-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8ca97-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8ca97-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
