---
title: ICorDebugSymbolProvider::GetCodeRange Method
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18fd8fdf9bcfa20b686ad1f04cd8dcc3b1c26de2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964643"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="c3cba-102">ICorDebugSymbolProvider::GetCodeRange Method</span><span class="sxs-lookup"><span data-stu-id="c3cba-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="c3cba-103">Pobiera adres początkowy i rozmiar metody z przyznanym adresem wirtualnym (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="c3cba-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3cba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3cba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3cba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3cba-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c3cba-106">podczas Względny adres wirtualny (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="c3cba-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="c3cba-107">określoną Wskaźnik na adres początkowy metody.</span><span class="sxs-lookup"><span data-stu-id="c3cba-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="c3cba-108">Wskaźnik do rozmiaru kodu metody (liczba bajtów kodu metody).</span><span class="sxs-lookup"><span data-stu-id="c3cba-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3cba-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3cba-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3cba-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3cba-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3cba-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3cba-111">Requirements</span></span>  
 <span data-ttu-id="c3cba-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3cba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3cba-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3cba-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3cba-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3cba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3cba-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3cba-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cba-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3cba-116">See also</span></span>

- [<span data-ttu-id="c3cba-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3cba-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c3cba-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3cba-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
