---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ef8d1c47275d3cbd69c1516b788b950f8535513
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737715"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="5a34e-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a34e-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="5a34e-103">Pobiera moduł wyliczający dla pamięci podręcznej typów środowiska wykonawczego Windows w domenie aplikacji, w oparciu o ich identyfikatory interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5a34e-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a34e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a34e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a34e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a34e-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="5a34e-106">[in] Liczba wymaganych typów.</span><span class="sxs-lookup"><span data-stu-id="5a34e-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="5a34e-107">[in] Wskaźnik do tablicy, która zawiera identyfikatory interfejsu odpowiadający zarządzanych reprezentacja typów środowiska wykonawczego Windows, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="5a34e-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="5a34e-108">[out] Wskaźnik na adres obiektu interfejsu "icordebugtypeenum —", który umożliwia wyliczenie zarządzanej pamięci podręcznej reprezentacja typów środowiska wykonawczego Windows pobierane, oparte na identyfikatory interfejsu w `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="5a34e-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a34e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a34e-109">Remarks</span></span>  
 <span data-ttu-id="5a34e-110">Jeśli metoda nie można pobrać informacji dla identyfikatora określonego interfejsu, odpowiadający mu wpis w kolekcji "Icordebugtypeenum —" będzie mieć typ `ELEMENT_TYPE_END` błędy z powodu problemów z pobierania danych, lub `ELEMENT_TYPE_VOID` dla nieznanego interfejsu identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="5a34e-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a34e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a34e-111">Requirements</span></span>  
 <span data-ttu-id="5a34e-112">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a34e-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="5a34e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a34e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a34e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a34e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a34e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a34e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a34e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a34e-116">See also</span></span>

- [<span data-ttu-id="5a34e-117">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a34e-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
