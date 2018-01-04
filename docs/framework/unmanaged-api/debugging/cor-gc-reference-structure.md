---
title: "COR_GC_REFERENCE — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86604febb7641eef147608e564a27883fdc4bec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreference-structure"></a><span data-ttu-id="2dfcb-102">COR_GC_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="2dfcb-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="2dfcb-103">Zawiera informacje dotyczące obiektu, który ma być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dfcb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2dfcb-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="2dfcb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2dfcb-105">Members</span></span>  
  
|<span data-ttu-id="2dfcb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2dfcb-106">Member</span></span>|<span data-ttu-id="2dfcb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2dfcb-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="2dfcb-108">Wskaźnik do domeny aplikacji, do której należy dany dojścia lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="2dfcb-109">Wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="2dfcb-110">ICorDebugValue lub ICorDebugReferenceValue — interfejs umożliwiająca obiektu ma być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="2dfcb-111">A [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartość wyliczenia wskazująca, skąd pochodzą katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="2dfcb-112">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="2dfcb-113">Dodatkowe dane dotyczące obiektu ma być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="2dfcb-114">Te informacje jest zależny od źródła obiektu, wskazywany przez `type` pola.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="2dfcb-115">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dfcb-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2dfcb-116">Remarks</span></span>  
 <span data-ttu-id="2dfcb-117">`type` Pole jest [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartość wyliczenia wskazująca, skąd pochodzą odwołania.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="2dfcb-118">Określonego `COR_GC_REFERENCE` wartości można odzwierciedlać dowolną z następujących typów obiektów zarządzanych:</span><span class="sxs-lookup"><span data-stu-id="2dfcb-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
-   <span data-ttu-id="2dfcb-119">Obiekty z wszystkie zarządzane stosy (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="2dfcb-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="2dfcb-120">Dotyczy to na żywo odwołuje się do kodu zarządzanego, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="2dfcb-121">Obiekty z tabeli dojścia (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="2dfcb-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="2dfcb-122">W tym silne odwołań (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmienne statyczne w module.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="2dfcb-123">Obiekty w kolejce finalizatora (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="2dfcb-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="2dfcb-124">Kolejce finalizatora katalogów głównych obiektów, do momentu finalizator zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="2dfcb-125">`extraData` Pole zawiera dodatkowe dane w zależności od źródłowego (lub typ) odwołanie.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="2dfcb-126">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2dfcb-126">Possible values are:</span></span>  
  
-   <span data-ttu-id="2dfcb-127">`DependentSource`.,</span><span class="sxs-lookup"><span data-stu-id="2dfcb-127">`DependentSource`.</span></span> <span data-ttu-id="2dfcb-128">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiekt, który jeśli aktywności, katalogów głównych obiektu ma być pobrane pamięci w `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
-   <span data-ttu-id="2dfcb-129">`RefCount`.,</span><span class="sxs-lookup"><span data-stu-id="2dfcb-129">`RefCount`.</span></span> <span data-ttu-id="2dfcb-130">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczba odwołań uchwytu.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
-   <span data-ttu-id="2dfcb-131">`Size`.,</span><span class="sxs-lookup"><span data-stu-id="2dfcb-131">`Size`.</span></span> <span data-ttu-id="2dfcb-132">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiar drzewa obiektów, dla którego moduł zbierający elementy bezużyteczne obliczana katalogów głównych obiektów.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="2dfcb-133">Należy zwrócić uwagę, to obliczenie nie jest zawsze aktualny.</span><span class="sxs-lookup"><span data-stu-id="2dfcb-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dfcb-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2dfcb-134">Requirements</span></span>  
 <span data-ttu-id="2dfcb-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dfcb-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dfcb-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2dfcb-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2dfcb-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2dfcb-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dfcb-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dfcb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dfcb-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dfcb-139">See Also</span></span>  
 [<span data-ttu-id="2dfcb-140">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="2dfcb-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="2dfcb-141">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2dfcb-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
