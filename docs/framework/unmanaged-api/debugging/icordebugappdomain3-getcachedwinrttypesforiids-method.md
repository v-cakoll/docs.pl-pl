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
ms.openlocfilehash: 95c84f7f40db0096b26ec448f8f229cdbfe3afb1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025908"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="2a03f-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a03f-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="2a03f-103">Pobiera moduł wyliczający dla pamięci podręcznej typów środowiska wykonawczego Windows w domenie aplikacji, w oparciu o ich identyfikatory interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2a03f-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a03f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a03f-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a03f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a03f-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="2a03f-106">[in] Liczba wymaganych typów.</span><span class="sxs-lookup"><span data-stu-id="2a03f-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="2a03f-107">[in] Wskaźnik do tablicy, która zawiera identyfikatory interfejsu odpowiadający zarządzanych reprezentacja typów środowiska wykonawczego Windows, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="2a03f-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="2a03f-108">[out] Wskaźnik na adres obiektu interfejsu "icordebugtypeenum —", który umożliwia wyliczenie zarządzanej pamięci podręcznej reprezentacja typów środowiska wykonawczego Windows pobierane, oparte na identyfikatory interfejsu w `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="2a03f-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a03f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a03f-109">Remarks</span></span>  
 <span data-ttu-id="2a03f-110">Jeśli metoda nie można pobrać informacji dla identyfikatora określonego interfejsu, odpowiadający mu wpis w kolekcji "Icordebugtypeenum —" będzie mieć typ `ELEMENT_TYPE_END` błędy z powodu problemów z pobierania danych, lub `ELEMENT_TYPE_VOID` dla nieznanego interfejsu identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="2a03f-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a03f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a03f-111">Requirements</span></span>  
 <span data-ttu-id="2a03f-112">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2a03f-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="2a03f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a03f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a03f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a03f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a03f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a03f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a03f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a03f-116">See also</span></span>

- [<span data-ttu-id="2a03f-117">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a03f-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
