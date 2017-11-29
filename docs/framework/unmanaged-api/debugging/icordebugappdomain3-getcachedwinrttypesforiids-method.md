---
title: "ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84b58e3a016431eba10710ea384338cb388404ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="94f5a-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="94f5a-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="94f5a-103">Pobiera moduł wyliczający dla pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów w domenie aplikacji w oparciu o ich identyfikatorów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="94f5a-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94f5a-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94f5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94f5a-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="94f5a-106">[in] Liczba wymaganych typów.</span><span class="sxs-lookup"><span data-stu-id="94f5a-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="94f5a-107">[in] Wskaźnik do tablicy zawiera identyfikatory interfejsu odpowiadającego zarządzanych reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="94f5a-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="94f5a-108">[out] Wskaźnik do obiektu interfejsu "ICorDebugTypeEnum", który umożliwia wyliczenie zapisane w pamięci podręcznej adres zarządzane reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] pobrać typy oparte na identyfikatorach interfejsu w `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="94f5a-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94f5a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94f5a-109">Remarks</span></span>  
 <span data-ttu-id="94f5a-110">Jeśli metoda nie można pobrać informacji o identyfikator określonego interfejsu, odpowiadający mu wpis w kolekcji "ICorDebugTypeEnum" będzie mieć typ `ELEMENT_TYPE_END` błędy z powodu problemów pobierania danych, lub `ELEMENT_TYPE_VOID` dla nieznanego interfejsu identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="94f5a-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f5a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94f5a-111">Requirements</span></span>  
 <span data-ttu-id="94f5a-112">**Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94f5a-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="94f5a-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94f5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94f5a-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94f5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94f5a-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94f5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f5a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94f5a-116">See Also</span></span>  
 [<span data-ttu-id="94f5a-117">ICorDebugAppDomain3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="94f5a-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
