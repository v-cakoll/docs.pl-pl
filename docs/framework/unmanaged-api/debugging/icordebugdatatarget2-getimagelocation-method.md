---
title: Metoda ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7acf08262c73df00a96cfb5c244cdfc352e51ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789756"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="e9e44-102">Metoda ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="e9e44-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="e9e44-103">Zwraca ścieżkę modułu z adresu podstawowego modułu.</span><span class="sxs-lookup"><span data-stu-id="e9e44-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9e44-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9e44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9e44-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="e9e44-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres bazowy modułu.</span><span class="sxs-lookup"><span data-stu-id="e9e44-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e9e44-107">[in] Liczba znaków w buforze, który ma otrzymać ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="e9e44-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e9e44-108">[out] Wskaźnik do liczby znaków zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="e9e44-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e9e44-109">[out] Ścieżka do modułu.</span><span class="sxs-lookup"><span data-stu-id="e9e44-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9e44-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9e44-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9e44-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e9e44-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e44-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9e44-112">Requirements</span></span>  
 <span data-ttu-id="e9e44-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9e44-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9e44-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9e44-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9e44-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9e44-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9e44-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e44-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e44-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9e44-117">See also</span></span>

- [<span data-ttu-id="e9e44-118">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9e44-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="e9e44-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e9e44-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
