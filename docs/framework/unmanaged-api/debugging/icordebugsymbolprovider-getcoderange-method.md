---
title: ICorDebugSymbolProvider::GetCodeRange Method
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52fd0e9dac1d255197909d153099d9c6f2bd8ff7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212937"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="fd8e1-102">ICorDebugSymbolProvider::GetCodeRange Method</span><span class="sxs-lookup"><span data-stu-id="fd8e1-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="fd8e1-103">Pobiera adres początkowy metody i biorąc względnych adresów wirtualnych (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="fd8e1-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd8e1-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd8e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd8e1-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="fd8e1-106">[in] Wirtualny adres względny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="fd8e1-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="fd8e1-107">[out] Wskaźnik do adres początkowy metody.</span><span class="sxs-lookup"><span data-stu-id="fd8e1-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="fd8e1-108">Wskaźnik do rozmiaru kodu — metoda (liczba bajtów kodu metody).</span><span class="sxs-lookup"><span data-stu-id="fd8e1-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd8e1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd8e1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd8e1-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd8e1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8e1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd8e1-111">Requirements</span></span>  
 <span data-ttu-id="fd8e1-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd8e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8e1-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd8e1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd8e1-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd8e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd8e1-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8e1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8e1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd8e1-116">See also</span></span>

- [<span data-ttu-id="fd8e1-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd8e1-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="fd8e1-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fd8e1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
