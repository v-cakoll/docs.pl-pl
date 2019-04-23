---
title: Metoda ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7acf08262c73df00a96cfb5c244cdfc352e51ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080484"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="4be3e-102">Metoda ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="4be3e-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="4be3e-103">Zwraca ścieżkę modułu z adresu podstawowego modułu.</span><span class="sxs-lookup"><span data-stu-id="4be3e-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4be3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4be3e-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4be3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4be3e-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="4be3e-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres bazowy modułu.</span><span class="sxs-lookup"><span data-stu-id="4be3e-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4be3e-107">[in] Liczba znaków w buforze, który ma otrzymać ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="4be3e-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4be3e-108">[out] Wskaźnik do liczby znaków zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="4be3e-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="4be3e-109">[out] Ścieżka do modułu.</span><span class="sxs-lookup"><span data-stu-id="4be3e-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4be3e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4be3e-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4be3e-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4be3e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4be3e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4be3e-112">Requirements</span></span>  
 <span data-ttu-id="4be3e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4be3e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4be3e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4be3e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4be3e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4be3e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4be3e-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4be3e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be3e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4be3e-117">See also</span></span>

- [<span data-ttu-id="4be3e-118">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4be3e-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="4be3e-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4be3e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
