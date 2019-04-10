---
title: IMetaDataEmit::MergeEnd — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277e7e57ae01128039c3a280158110acde3363a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230008"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="4b654-102">IMetaDataEmit::MergeEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b654-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="4b654-103">Scala do bieżącego zakresu zakresy metadanych określone przez co najmniej jeden poprzedniego wywołania [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="4b654-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b654-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b654-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b654-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b654-105">Parameters</span></span>  
 <span data-ttu-id="4b654-106">Ta metoda nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="4b654-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b654-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b654-107">Remarks</span></span>  
 <span data-ttu-id="4b654-108">Ta procedura wyzwala rzeczywiste Scalanie metadanych, wszystkich Importuj zakresy określone w tym celu przed wywołania `IMetaDataEmit::Merge`, w bieżącym zakresie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4b654-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="4b654-109">Scalenie stosują się następujące warunki specjalne:</span><span class="sxs-lookup"><span data-stu-id="4b654-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="4b654-110">Identyfikator wersji modułu (identyfikatorem MVID) nigdy nie jest importowany, ponieważ jest on unikatowy dla metadanych w zakresie importowania.</span><span class="sxs-lookup"><span data-stu-id="4b654-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="4b654-111">Nie istniejących właściwości całego modułu zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="4b654-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="4b654-112">Jeśli moduł właściwości zostały skonfigurowane dla bieżącego zakresu, zostaną zaimportowane żadnych właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="4b654-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="4b654-113">Jednakże jeśli nie ustawiono właściwości modułu w bieżącym zakresie, zaimportowaniu tylko raz, po ich pierwszym napotkaniu.</span><span class="sxs-lookup"><span data-stu-id="4b654-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="4b654-114">Jeśli te właściwości modułu wystąpi ponownie, są one duplikaty.</span><span class="sxs-lookup"><span data-stu-id="4b654-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="4b654-115">Jeśli są porównywane wartości wszystkich właściwości modułu (z wyjątkiem identyfikatora MVID) i duplikaty nie zostaną znalezione, zgłaszany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="4b654-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="4b654-116">Aby uzyskać definicje typów (`TypeDef`), bez duplikatów są scalane w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="4b654-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> `TypeDef` <span data-ttu-id="4b654-117">obiekty są sprawdzane duplikatów w odniesieniu do każdego *obiektu w pełni kwalifikowana nazwa* + *GUID* + *numer wersji*.</span><span class="sxs-lookup"><span data-stu-id="4b654-117">objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="4b654-118">Jeśli są zgodne na nazwę lub identyfikator GUID i inne elementy są różne, zgłaszany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="4b654-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="4b654-119">W przeciwnym razie, jeśli wszystkie trzy elementy są zgodne, `MergeEnd` wykonuje sprawdzenie pobieżną, aby upewnić się, wpisy są rzeczywiście duplikaty; w przeciwnym razie występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="4b654-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="4b654-120">To sprawdzenie pobieżną szuka:</span><span class="sxs-lookup"><span data-stu-id="4b654-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="4b654-121">Ten sam element członkowski deklaracji, pojawiają się w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4b654-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="4b654-122">Elementy członkowskie, które są oznaczane jako `mdPrivateScope` (zobacz [cormethodattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie) nie są uwzględnione w tym wyboru; są one scalane specjalnie.</span><span class="sxs-lookup"><span data-stu-id="4b654-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="4b654-123">Taki sam układ klasy.</span><span class="sxs-lookup"><span data-stu-id="4b654-123">The same class layout.</span></span>  
  
     <span data-ttu-id="4b654-124">Oznacza to, że `TypeDef` obiektu muszą zawsze być spójnie i w pełni zdefiniowana w każdym zakresie metadanych w której jest zadeklarowana; jeśli jego implementacji elementu członkowskiego (dla klasy) są rozmieszczone w wielu jednostkach kompilacji, pełna definicja zakłada się, że obecny w każdym zakresie, a nie przyrostowa każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="4b654-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="4b654-125">Na przykład jeśli nazwy parametrów są istotne dla kontraktu, ich musi być emitowane taki sam sposób do każdego zakresu; Jeśli nie są istotne, nie należy ich wydane do metadanych.</span><span class="sxs-lookup"><span data-stu-id="4b654-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="4b654-126">Wyjątkiem jest to, że `TypeDef` obiekt może mieć przyrostowe składowe oznaczone jako `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="4b654-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="4b654-127">Po wystąpieniu, `MergeEnd` przyrostowo dodaje je do bieżącego zakresu, bez względu na duplikaty.</span><span class="sxs-lookup"><span data-stu-id="4b654-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="4b654-128">Ponieważ kompilator rozpoznaje zakres prywatnych, kompilator musi być odpowiedzialne za wymuszanie stosowania zasad.</span><span class="sxs-lookup"><span data-stu-id="4b654-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="4b654-129">Względnych adresów wirtualnych (RVA) nie są importowane lub scalić; kompilator powinien ponownie wyemitować tych informacji.</span><span class="sxs-lookup"><span data-stu-id="4b654-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="4b654-130">Atrybuty niestandardowe są scalane, tylko wtedy, gdy jest scalany elementu, do której są dołączone.</span><span class="sxs-lookup"><span data-stu-id="4b654-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="4b654-131">Na przykład niestandardowe atrybuty powiązane z klasą zostaną scalone, po pierwszym napotkaniu klasy.</span><span class="sxs-lookup"><span data-stu-id="4b654-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="4b654-132">Jeśli atrybutów niestandardowych, które są skojarzone z `TypeDef` lub `MemberDef` jest specyficzne dla jednostki kompilacji (takich jak sygnatura czasowa kompilacji elementu członkowskiego), nie są one scalane i zależy od kompilator, aby usunąć lub zaktualizować takie metadane.</span><span class="sxs-lookup"><span data-stu-id="4b654-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b654-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b654-133">Requirements</span></span>  
 <span data-ttu-id="4b654-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b654-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b654-135">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4b654-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b654-136">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b654-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4b654-137">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4b654-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b654-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b654-138">See also</span></span>

- [<span data-ttu-id="4b654-139">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4b654-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4b654-140">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4b654-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
