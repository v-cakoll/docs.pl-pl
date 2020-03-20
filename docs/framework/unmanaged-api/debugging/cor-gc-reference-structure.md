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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179317"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="2c843-102">COR_GC_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="2c843-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="2c843-103">Zawiera informacje o obiekcie, który ma być zbierane śmieci.</span><span class="sxs-lookup"><span data-stu-id="2c843-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c843-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c843-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="2c843-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2c843-105">Members</span></span>  
  
|<span data-ttu-id="2c843-106">Członek</span><span class="sxs-lookup"><span data-stu-id="2c843-106">Member</span></span>|<span data-ttu-id="2c843-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2c843-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="2c843-108">Wskaźnik do domeny aplikacji, do której należy dojście lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="2c843-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="2c843-109">Jego wartość `null`może być .</span><span class="sxs-lookup"><span data-stu-id="2c843-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="2c843-110">Interfejs ICorDebugValue lub ICorDebugReferenceValue, który odpowiada obiektowi, który ma być zbierany z modułu.</span><span class="sxs-lookup"><span data-stu-id="2c843-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="2c843-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) wartość wyliczenia, która wskazuje, skąd pochodzi katalog główny.</span><span class="sxs-lookup"><span data-stu-id="2c843-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="2c843-112">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="2c843-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="2c843-113">Dodatkowe dane dotyczące obiektu, który ma być zbierany na śmieci.</span><span class="sxs-lookup"><span data-stu-id="2c843-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="2c843-114">Informacje te zależą od źródła obiektu, wskazanego `type` w polu.</span><span class="sxs-lookup"><span data-stu-id="2c843-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="2c843-115">Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.</span><span class="sxs-lookup"><span data-stu-id="2c843-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c843-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c843-116">Remarks</span></span>  
 <span data-ttu-id="2c843-117">Pole `type` jest wartością wyliczenia [CorGCReferenceType,](corgcreferencetype-enumeration.md) która wskazuje, skąd pochodzi odwołanie.</span><span class="sxs-lookup"><span data-stu-id="2c843-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="2c843-118">Określona `COR_GC_REFERENCE` wartość może odzwierciedlać dowolny z następujących rodzajów obiektów zarządzanych:</span><span class="sxs-lookup"><span data-stu-id="2c843-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="2c843-119">Obiekty ze wszystkich zarządzanych stosów (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="2c843-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="2c843-120">Obejmuje to odwołania na żywo w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="2c843-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="2c843-121">Obiekty z tabeli`CorGCReferenceType.CorHandle*`uchwytów ( ).</span><span class="sxs-lookup"><span data-stu-id="2c843-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="2c843-122">Obejmuje to silne`HNDTYPE_STRONG` odwołania `HNDTYPE_REFCOUNT`( i ) i zmienne statyczne w module.</span><span class="sxs-lookup"><span data-stu-id="2c843-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="2c843-123">Obiekty z kolejki finalizatorów (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="2c843-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="2c843-124">Obiekty główne kolejki finalizacji, dopóki finalizator nie zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="2c843-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="2c843-125">To `extraData` pole zawiera dodatkowe dane w zależności od źródła (lub typu) odwołania.</span><span class="sxs-lookup"><span data-stu-id="2c843-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="2c843-126">Możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="2c843-126">Possible values are:</span></span>  
  
- <span data-ttu-id="2c843-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="2c843-127">`DependentSource`.</span></span> <span data-ttu-id="2c843-128">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiektem, który, jeśli żyje, `COR_GC_REFERENCE.Location`korzenie obiektu mają być zbierane w odpadach w .</span><span class="sxs-lookup"><span data-stu-id="2c843-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="2c843-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="2c843-129">`RefCount`.</span></span> <span data-ttu-id="2c843-130">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczbą odwołań dojścia.</span><span class="sxs-lookup"><span data-stu-id="2c843-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="2c843-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="2c843-131">`Size`.</span></span> <span data-ttu-id="2c843-132">Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiarem drzewa obiektów, dla którego moduł zbierający elementy bezużyteczne obliczył katalogi główne obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c843-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="2c843-133">Należy zauważyć, że to obliczenie niekoniecznie jest aktualne.</span><span class="sxs-lookup"><span data-stu-id="2c843-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c843-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c843-134">Requirements</span></span>  
 <span data-ttu-id="2c843-135">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c843-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c843-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c843-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c843-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c843-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c843-138">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c843-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c843-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c843-139">See also</span></span>

- [<span data-ttu-id="2c843-140">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="2c843-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="2c843-141">Debugging</span><span class="sxs-lookup"><span data-stu-id="2c843-141">Debugging</span></span>](index.md)
