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
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179064"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="3395a-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="3395a-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="3395a-103">Pobiera moduł wyliczacza dla buforowanych typów środowiska wykonawczego systemu Windows w domenie aplikacji na podstawie ich identyfikatorów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3395a-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3395a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3395a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3395a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3395a-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="3395a-106">[w] Liczba wymaganych typów.</span><span class="sxs-lookup"><span data-stu-id="3395a-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="3395a-107">[w] Wskaźnik do tablicy zawierającej identyfikatory interfejsu odpowiadające zarządzanym reprezentacjom typów środowiska wykonawczego systemu Windows do pobrania.</span><span class="sxs-lookup"><span data-stu-id="3395a-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="3395a-108">[na zewnątrz] Wskaźnik do adresu obiektu interfejsu "ICorDebugTypeEnum", który umożliwia wyliczanie buforowanych zarządzanych reprezentacji pobranych typów środowiska wykonawczego `iidsToResolve`systemu Windows, na podstawie identyfikatorów interfejsu w programie .</span><span class="sxs-lookup"><span data-stu-id="3395a-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3395a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3395a-109">Remarks</span></span>  
 <span data-ttu-id="3395a-110">Jeśli metoda nie może pobrać informacji dla określonego identyfikatora interfejsu, odpowiedni wpis w kolekcji "ICorDebugTypeEnum" będzie miał `ELEMENT_TYPE_END` typ `ELEMENT_TYPE_VOID` błędów z powodu problemów z pobieraniem danych lub nieznanych identyfikatorów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3395a-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3395a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3395a-111">Requirements</span></span>  
 <span data-ttu-id="3395a-112">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3395a-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="3395a-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3395a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3395a-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3395a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3395a-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3395a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3395a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3395a-116">See also</span></span>

- [<span data-ttu-id="3395a-117">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="3395a-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
