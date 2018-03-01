---
title: "IMetaDataEmit::MergeEnd — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="d6995-102">IMetaDataEmit::MergeEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6995-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="d6995-103">Scalenia do bieżącego zakresu zakresy metadanych określonych przez jeden lub więcej poprzedniego wywołania [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="d6995-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6995-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6995-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6995-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6995-105">Parameters</span></span>  
 <span data-ttu-id="d6995-106">Ta metoda nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d6995-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6995-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6995-107">Remarks</span></span>  
 <span data-ttu-id="d6995-108">Ta procedura wyzwala rzeczywiste scalania metadanych, wszystkich import określono poprzedzając wywołań zakresów `IMetaDataEmit::Merge`, w bieżącym zakresie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d6995-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="d6995-109">Do scalania mają zastosowanie następujące warunki specjalne:</span><span class="sxs-lookup"><span data-stu-id="d6995-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="d6995-110">Identyfikator wersji modułu (identyfikatora MVID) nigdy nie zostaną zaimportowane, ponieważ jest unikatowa w zakresie importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d6995-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="d6995-111">Żadne istniejące właściwości modułu całej zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="d6995-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="d6995-112">Jeśli moduł właściwości zostały już skonfigurowane dla bieżącego zakresu, Brak właściwości modułu zostaną zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="d6995-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="d6995-113">Jednak jeśli nie ustawiono właściwości modułu w bieżącym zakresie, są one importowane tylko raz, gdy są najpierw napotkano.</span><span class="sxs-lookup"><span data-stu-id="d6995-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="d6995-114">Jeśli te właściwości modułu wystąpi ponownie, znajdują się duplikaty.</span><span class="sxs-lookup"><span data-stu-id="d6995-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="d6995-115">Jeśli znajdują się duplikaty nie są porównywane wartości wszystkich właściwości modułu (z wyjątkiem identyfikatora MVID), występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="d6995-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="d6995-116">Dla definicji typów (`TypeDef`), bez duplikatów są scalane w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d6995-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="d6995-117">`TypeDef`obiekty są sprawdzane pod kątem duplikatów dla każdego *obiektu w pełni kwalifikowaną nazwę* + *GUID* + *numer wersji*.</span><span class="sxs-lookup"><span data-stu-id="d6995-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="d6995-118">Jeśli są zgodne na nazwę lub identyfikator GUID i inne elementy są różne, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="d6995-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="d6995-119">W przeciwnym razie, jeśli wszystkie trzy elementy są zgodne, `MergeEnd` sprawdza pobieżną zapewnienie wpisy są rzeczywiście duplikaty; Jeśli nie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="d6995-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="d6995-120">Szuka tego pobieżnego:</span><span class="sxs-lookup"><span data-stu-id="d6995-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="d6995-121">Tego samego elementu członkowskiego deklaracjami występujących w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d6995-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="d6995-122">Elementy członkowskie, które są oznaczone jako `mdPrivateScope` (zobacz [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie) nie są uwzględnione w tym wyboru; są one scalane specjalnie.</span><span class="sxs-lookup"><span data-stu-id="d6995-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="d6995-123">Ten sam układ klasy.</span><span class="sxs-lookup"><span data-stu-id="d6995-123">The same class layout.</span></span>  
  
     <span data-ttu-id="d6995-124">Oznacza to, że `TypeDef` obiektu musi zawsze być w pełni i stale zdefiniowana w co zakres metadanych w którym zadeklarowany jest; jeśli jego implementacje elementów członkowskich (dla klasy) są rozkładane w wielu jednostkach kompilacji, pełnej definicji zakłada się, że w każdym zakresem i nie przyrostowe do każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="d6995-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="d6995-125">Na przykład jeśli nazwy parametrów mają zastosowanie do Umowy, ich musi być wydane tak samo do każdego zakresu; Jeśli nie są istotne, nie powinny one wydane do metadanych.</span><span class="sxs-lookup"><span data-stu-id="d6995-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="d6995-126">Wyjątkiem jest to, że `TypeDef` obiekt może mieć przyrostowe elementy członkowskie oznaczone jako `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="d6995-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="d6995-127">Po wystąpieniu, `MergeEnd` przyrostowo dodaje je do bieżącego zakresu bez względu na duplikaty.</span><span class="sxs-lookup"><span data-stu-id="d6995-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="d6995-128">Ponieważ kompilator rozumie zakres prywatny, kompilator musi być odpowiedzialny za egzekwowanie zasad.</span><span class="sxs-lookup"><span data-stu-id="d6995-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="d6995-129">Względne wirtualnych adresów (RVAs) nie są importowane lub scalić; kompilator powinien ponownie wyemitować tych informacji.</span><span class="sxs-lookup"><span data-stu-id="d6995-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="d6995-130">Atrybuty niestandardowe są scalane, tylko wtedy, gdy scalonego elementu, do której są dołączone.</span><span class="sxs-lookup"><span data-stu-id="d6995-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="d6995-131">Na przykład niestandardowe atrybuty powiązane z klasą są łączone przy pierwszym napotkaniu klasy.</span><span class="sxs-lookup"><span data-stu-id="d6995-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="d6995-132">Jeśli atrybutów niestandardowych, które są skojarzone z `TypeDef` lub `MemberDef` która jest specyficzna dla jednostki kompilacji (na przykład sygnaturę czasową kompilacji elementu członkowskiego), nie są one scalane i zależy od kompilator, aby usunąć lub zaktualizować takich metadanych.</span><span class="sxs-lookup"><span data-stu-id="d6995-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6995-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6995-133">Requirements</span></span>  
 <span data-ttu-id="d6995-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6995-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6995-135">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6995-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6995-136">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6995-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6995-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6995-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6995-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6995-138">See Also</span></span>  
 [<span data-ttu-id="d6995-139">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6995-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d6995-140">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6995-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
