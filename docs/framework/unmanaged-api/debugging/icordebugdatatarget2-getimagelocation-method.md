---
title: Metoda ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b046a5fcd514dde84e2f0f8c22ee23529ee906e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911469"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="427a1-102">Metoda ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="427a1-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="427a1-103">Zwraca ścieżkę modułu z adresu podstawowego modułu.</span><span class="sxs-lookup"><span data-stu-id="427a1-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="427a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="427a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="427a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="427a1-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="427a1-106">podczas Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="427a1-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="427a1-107">podczas Liczba znaków w buforze, która ma otrzymać ścieżkę modułu.</span><span class="sxs-lookup"><span data-stu-id="427a1-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="427a1-108">określoną Wskaźnik do liczby znaków zapisanych w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="427a1-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="427a1-109">określoną Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="427a1-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="427a1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="427a1-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="427a1-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="427a1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="427a1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="427a1-112">Requirements</span></span>  
 <span data-ttu-id="427a1-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="427a1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="427a1-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="427a1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="427a1-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="427a1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="427a1-116">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="427a1-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427a1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="427a1-117">See also</span></span>

- [<span data-ttu-id="427a1-118">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="427a1-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="427a1-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="427a1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
