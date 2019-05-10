---
title: COR_GC_REFERENCE — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 848765a4ea9657020bd84e476f992ae69750dda9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617695"
---
# <a name="corgcreference-structure"></a><span data-ttu-id="e9faa-102">COR_GC_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="e9faa-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="e9faa-103">Zawiera informacje dotyczące obiektu, który ma być zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e9faa-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9faa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9faa-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="e9faa-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e9faa-105">Members</span></span>  
  
|<span data-ttu-id="e9faa-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e9faa-106">Member</span></span>|<span data-ttu-id="e9faa-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e9faa-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="e9faa-108">Wskaźnik do domeny aplikacji, do której należy dany dojścia lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9faa-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="e9faa-109">Wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="e9faa-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="e9faa-110">ICorDebugValue lub icordebugreferencevalue — interfejs, który odnosi się do obiektu, aby być zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e9faa-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="e9faa-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartość wyliczenia, która wskazuje, skąd pochodzą katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="e9faa-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="e9faa-112">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="e9faa-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="e9faa-113">Dodatkowe dane dotyczące obiekt zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e9faa-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="e9faa-114">Te informacje zależy od źródła obiektu, wskazane przez `type` pola.</span><span class="sxs-lookup"><span data-stu-id="e9faa-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="e9faa-115">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="e9faa-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9faa-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9faa-116">Remarks</span></span>  
 <span data-ttu-id="e9faa-117">`type` Pole jest [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartości wyliczenia, która wskazuje, skąd pochodzą odwołania.</span><span class="sxs-lookup"><span data-stu-id="e9faa-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="e9faa-118">Konkretny `COR_GC_REFERENCE` wartość może odzwierciedlać jedną z następujących rodzajów obiekty zarządzane:</span><span class="sxs-lookup"><span data-stu-id="e9faa-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="e9faa-119">Obiekty z wszystkie stosy zarządzane (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="e9faa-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="e9faa-120">Obejmuje to odwołań na żywo w kodu zarządzanego, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e9faa-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="e9faa-121">Obiekty z tabelę uchwytów (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="e9faa-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="e9faa-122">Obejmuje to odwołań do silnych (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmiennych statycznych w module.</span><span class="sxs-lookup"><span data-stu-id="e9faa-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="e9faa-123">Obiekty z; kolejka finalizatorów (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="e9faa-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="e9faa-124">Elementy główne obiektów; kolejka finalizatorów, aż finalizator zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="e9faa-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="e9faa-125">`extraData` Pole zawiera dane dodatkowe, w zależności od źródła (lub typ) odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e9faa-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="e9faa-126">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e9faa-126">Possible values are:</span></span>  
  
- <span data-ttu-id="e9faa-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="e9faa-127">`DependentSource`.</span></span> <span data-ttu-id="e9faa-128">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiekt, który, jeśli jest aktywny, elementy główne obiekt zebranych elementów bezużytecznych w `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="e9faa-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="e9faa-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="e9faa-129">`RefCount`.</span></span> <span data-ttu-id="e9faa-130">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest licznik odwołań uchwytu.</span><span class="sxs-lookup"><span data-stu-id="e9faa-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="e9faa-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="e9faa-131">`Size`.</span></span> <span data-ttu-id="e9faa-132">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiar drzewa obiektów, dla którego moduł zbierający elementy bezużyteczne obliczana korzenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="e9faa-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="e9faa-133">Należy pamiętać, że to obliczenie nie zawsze aktualne.</span><span class="sxs-lookup"><span data-stu-id="e9faa-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9faa-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9faa-134">Requirements</span></span>  
 <span data-ttu-id="e9faa-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9faa-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9faa-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9faa-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9faa-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9faa-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9faa-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9faa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9faa-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9faa-139">See also</span></span>

- [<span data-ttu-id="e9faa-140">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="e9faa-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="e9faa-141">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e9faa-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
