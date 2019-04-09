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
ms.openlocfilehash: ed1d7ad95b7c8474121994d0f54557c1c36cb531
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095129"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="1858d-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="1858d-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="1858d-103">Pobiera moduł wyliczający dla pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów w domenie aplikacji w oparciu o ich identyfikatory interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1858d-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1858d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1858d-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1858d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1858d-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="1858d-106">[in] Liczba wymaganych typów.</span><span class="sxs-lookup"><span data-stu-id="1858d-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="1858d-107">[in] Wskaźnik do tablicy, który zawiera identyfikatory interfejsu odpowiadający reprezentacje zarządzane [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="1858d-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="1858d-108">[out] Wskaźnik na adres obiektu interfejsu "icordebugtypeenum —", który umożliwia wyliczenie buforowane zarządzane reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] pobierane typy, oparte na identyfikatory interfejsu w `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="1858d-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1858d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1858d-109">Remarks</span></span>  
 <span data-ttu-id="1858d-110">Jeśli metoda nie można pobrać informacji dla identyfikatora określonego interfejsu, odpowiadający mu wpis w kolekcji "Icordebugtypeenum —" będzie mieć typ `ELEMENT_TYPE_END` błędy z powodu problemów z pobierania danych, lub `ELEMENT_TYPE_VOID` dla nieznanego interfejsu identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="1858d-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1858d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1858d-111">Requirements</span></span>  
 **<span data-ttu-id="1858d-112">Platformy:</span><span class="sxs-lookup"><span data-stu-id="1858d-112">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="1858d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1858d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1858d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1858d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1858d-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1858d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1858d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1858d-116">See also</span></span>

- [<span data-ttu-id="1858d-117">ICorDebugAppDomain3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1858d-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
