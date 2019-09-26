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
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274224"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="ddcd3-102">COR_GC_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="ddcd3-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="ddcd3-103">Zawiera informacje o obiekcie, który ma zostać pobrany do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcd3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddcd3-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="ddcd3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ddcd3-105">Members</span></span>  
  
|<span data-ttu-id="ddcd3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ddcd3-106">Member</span></span>|<span data-ttu-id="ddcd3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ddcd3-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="ddcd3-108">Wskaźnik do domeny aplikacji, do której należy dojście lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="ddcd3-109">Jego wartość może być `null`równa.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="ddcd3-110">Interfejs ICorDebugValue lub ICorDebugReferenceValue, który odnosi się do obiektu, który ma zostać pobrany jako bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="ddcd3-111">Wartość wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) , która wskazuje, skąd pochodzi element główny.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="ddcd3-112">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="ddcd3-113">Dodatkowe dane dotyczące obiektu, który ma zostać pobrany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="ddcd3-114">Te informacje są zależne od źródła obiektu, jak wskazano `type` w polu.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="ddcd3-115">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddcd3-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddcd3-116">Remarks</span></span>  
 <span data-ttu-id="ddcd3-117">Pole to CorGCReferenceType wartość wyliczenia, która wskazuje, skąd pochodzi odwołanie. [](corgcreferencetype-enumeration.md) `type`</span><span class="sxs-lookup"><span data-stu-id="ddcd3-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="ddcd3-118">Określona `COR_GC_REFERENCE` wartość może odzwierciedlać dowolny z następujących rodzajów obiektów zarządzanych:</span><span class="sxs-lookup"><span data-stu-id="ddcd3-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="ddcd3-119">Obiekty ze wszystkich stosów zarządzanych`CorGCReferenceType.CorReferenceStack`().</span><span class="sxs-lookup"><span data-stu-id="ddcd3-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="ddcd3-120">Obejmuje to dynamiczne odwołania w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="ddcd3-121">Obiekty z tabeli uchwytów (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="ddcd3-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="ddcd3-122">Obejmuje to ścisłe odwołania`HNDTYPE_STRONG` ( `HNDTYPE_REFCOUNT`i) oraz zmienne statyczne w module.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="ddcd3-123">Obiekty z kolejki finalizatora (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="ddcd3-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="ddcd3-124">Obiekty główne kolejki finalizatora do momentu uruchomienia finalizatora.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="ddcd3-125">`extraData` Pole zawiera dodatkowe dane w zależności od źródła (lub typu) odwołania.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="ddcd3-126">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ddcd3-126">Possible values are:</span></span>  
  
- <span data-ttu-id="ddcd3-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-127">`DependentSource`.</span></span> <span data-ttu-id="ddcd3-128">Jeśli jest, `CorGCREferenceType.CorHandleStrongDependent`to pole jest obiektem, który, jeśli działa, jest katalogiem głównym obiektu, który ma `COR_GC_REFERENCE.Location`zostać odrzucony. `type`</span><span class="sxs-lookup"><span data-stu-id="ddcd3-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="ddcd3-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-129">`RefCount`.</span></span> <span data-ttu-id="ddcd3-130">`type` Jeśli jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczbą odwołań do dojścia.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="ddcd3-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-131">`Size`.</span></span> <span data-ttu-id="ddcd3-132">`type` Jeśli jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiarem drzewa obiektów, dla którego Moduł wyrzucania elementów bezużytecznych oblicza elementy główne obiektu.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="ddcd3-133">Należy zauważyć, że to obliczenie nie jest zawsze aktualne.</span><span class="sxs-lookup"><span data-stu-id="ddcd3-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcd3-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddcd3-134">Requirements</span></span>  
 <span data-ttu-id="ddcd3-135">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcd3-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcd3-136">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddcd3-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddcd3-137">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddcd3-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddcd3-138">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcd3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcd3-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcd3-139">See also</span></span>

- [<span data-ttu-id="ddcd3-140">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="ddcd3-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ddcd3-141">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ddcd3-141">Debugging</span></span>](index.md)
