---
title: Metoda ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6962c8063479b3b0279d771b1b0cd1df63f696b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="08a38-102">Metoda ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="08a38-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="08a38-103">Zwraca ścieżkę modułu z adresem podstawowym modułu.</span><span class="sxs-lookup"><span data-stu-id="08a38-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08a38-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08a38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08a38-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="08a38-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="08a38-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="08a38-107">[in] Liczba znaków w buforze, który ma otrzymać ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="08a38-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="08a38-108">[out] Wskaźnik do liczby znaków zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="08a38-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="08a38-109">[out] Ścieżka do modułu.</span><span class="sxs-lookup"><span data-stu-id="08a38-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08a38-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08a38-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08a38-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="08a38-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a38-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08a38-112">Requirements</span></span>  
 <span data-ttu-id="08a38-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08a38-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a38-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08a38-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08a38-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08a38-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08a38-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a38-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a38-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08a38-117">See Also</span></span>  
 [<span data-ttu-id="08a38-118">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="08a38-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="08a38-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="08a38-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
