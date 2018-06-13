---
title: ICorDebugSymbolProvider::GetCodeRange — metoda
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60ba1c68e95363a59c5a1d217756664f63e5256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420127"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="9d5f2-102">ICorDebugSymbolProvider::GetCodeRange — metoda</span><span class="sxs-lookup"><span data-stu-id="9d5f2-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="9d5f2-103">Pobiera adres początkowy — metoda i rozmiar podany wirtualny adres względny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="9d5f2-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d5f2-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d5f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d5f2-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="9d5f2-106">[in] Wirtualny adres względny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="9d5f2-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="9d5f2-107">[out] Wskaźnik do metody adres początkowy.</span><span class="sxs-lookup"><span data-stu-id="9d5f2-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="9d5f2-108">Wskaźnik do rozmiaru kodu — metoda (liczba bajtów kod metody).</span><span class="sxs-lookup"><span data-stu-id="9d5f2-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d5f2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d5f2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d5f2-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9d5f2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d5f2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d5f2-111">Requirements</span></span>  
 <span data-ttu-id="9d5f2-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d5f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d5f2-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d5f2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d5f2-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d5f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d5f2-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d5f2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5f2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d5f2-116">See Also</span></span>  
 [<span data-ttu-id="9d5f2-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d5f2-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="9d5f2-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d5f2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
