---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bf09c01d24315c3f239911326f1844a0b2cc101
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111270"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="f77f8-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="f77f8-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="f77f8-103">Pobiera nazwę załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="f77f8-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f77f8-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f77f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f77f8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f77f8-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="f77f8-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f77f8-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="f77f8-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f77f8-108">[out] Tablica znaków, które zawierają nazwy załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="f77f8-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f77f8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f77f8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f77f8-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f77f8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f77f8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f77f8-111">Requirements</span></span>  
 <span data-ttu-id="f77f8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f77f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f77f8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f77f8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f77f8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f77f8-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f77f8-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f77f8-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f77f8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f77f8-116">See also</span></span>

- [<span data-ttu-id="f77f8-117">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="f77f8-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f77f8-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f77f8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
