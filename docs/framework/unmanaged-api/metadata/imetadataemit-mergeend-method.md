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
ms.openlocfilehash: feb81b86190f953b50f43f244f4e58a0a482f86e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003922"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="3bf29-102">IMetaDataEmit::MergeEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="3bf29-102">IMetaDataEmit::MergeEnd Method</span></span>

<span data-ttu-id="3bf29-103">Scala do bieżącego zakresu wszystkich zakresów metadanych określonych przez jedno lub więcej wcześniejszych wywołań do [IMetaDataEmit:: Merge](imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="3bf29-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](imetadataemit-merge-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="3bf29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bf29-104">Syntax</span></span>

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a><span data-ttu-id="3bf29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bf29-105">Parameters</span></span>

<span data-ttu-id="3bf29-106">Ta metoda nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="3bf29-106">This method takes no parameters.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bf29-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bf29-107">Remarks</span></span>

<span data-ttu-id="3bf29-108">Ta procedura wyzwala rzeczywiste scalanie metadanych wszystkich zakresów importu określonych przez poprzednie wywołania do `IMetaDataEmit::Merge` , do bieżącego zakresu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="3bf29-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>

<span data-ttu-id="3bf29-109">Następujące specjalne warunki dotyczą scalania:</span><span class="sxs-lookup"><span data-stu-id="3bf29-109">The following special conditions apply to the merge:</span></span>

- <span data-ttu-id="3bf29-110">Identyfikator wersji modułu (MVID) nigdy nie jest importowany, ponieważ jest unikatowy dla metadanych w zakresie importu.</span><span class="sxs-lookup"><span data-stu-id="3bf29-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>

- <span data-ttu-id="3bf29-111">Żadne istniejące właściwości całego modułu nie są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="3bf29-111">No existing module-wide properties are overwritten.</span></span>

  <span data-ttu-id="3bf29-112">Jeśli właściwości modułu zostały już ustawione dla bieżącego zakresu, nie zaimportowano żadnych właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="3bf29-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="3bf29-113">Jeśli jednak właściwości modułu nie zostały ustawione w bieżącym zakresie, są one importowane tylko raz podczas pierwszego napotkania.</span><span class="sxs-lookup"><span data-stu-id="3bf29-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="3bf29-114">Jeśli te właściwości modułu zostaną ponownie wykryte, są one duplikatami.</span><span class="sxs-lookup"><span data-stu-id="3bf29-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="3bf29-115">Jeśli wartości wszystkich właściwości modułu (z wyjątkiem MVID) są porównywane i nie znaleziono duplikatów, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="3bf29-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>

- <span data-ttu-id="3bf29-116">W przypadku definicji typu ( `TypeDef` ) żadne duplikaty nie są scalane z bieżącym zakresem.</span><span class="sxs-lookup"><span data-stu-id="3bf29-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="3bf29-117">`TypeDef`obiekty są sprawdzane pod kątem duplikatów dla każdej w *pełni kwalifikowanej nazwy obiektu*  +  *GUID*  +  *numeru wersji*.</span><span class="sxs-lookup"><span data-stu-id="3bf29-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="3bf29-118">Jeśli istnieje dopasowanie dla nazwy lub identyfikatora GUID, a którykolwiek z pozostałych dwóch elementów jest inny, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="3bf29-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="3bf29-119">W przeciwnym razie, jeśli wszystkie trzy elementy są zgodne, program `MergeEnd` sprawdza kursor, aby upewnić się, że wpisy są rzeczywiście duplikatami; Jeśli nie, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="3bf29-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="3bf29-120">Sprawdzanie kursorów szuka:</span><span class="sxs-lookup"><span data-stu-id="3bf29-120">This cursory check looks for:</span></span>

  - <span data-ttu-id="3bf29-121">Te same deklaracje elementu członkowskiego, występujące w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="3bf29-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="3bf29-122">Elementy członkowskie, które są oflagowane jako `mdPrivateScope` (zobacz Wyliczenie [CorMethodAttr —](cormethodattr-enumeration.md) ) nie są uwzględnione w tym sprawdzaniu; są scalane specjalnie.</span><span class="sxs-lookup"><span data-stu-id="3bf29-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>

  - <span data-ttu-id="3bf29-123">Ten sam układ klasy.</span><span class="sxs-lookup"><span data-stu-id="3bf29-123">The same class layout.</span></span>

  <span data-ttu-id="3bf29-124">Oznacza to, że `TypeDef` obiekt musi zawsze być w pełni i spójnie zdefiniowany w każdym zakresie metadanych, w którym jest zadeklarowany; jeśli jego implementacje składowe (dla klasy) są rozłożone w wielu jednostkach kompilacji, przyjmuje się, że wszystkie definicje są obecne w każdym zakresie i nie są przyrostowe dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="3bf29-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="3bf29-125">Na przykład jeśli nazwy parametrów są odpowiednie dla kontraktu, muszą one być emitowane w taki sam sposób do każdego zakresu; Jeśli nie są istotne, nie powinny być emitowane do metadanych.</span><span class="sxs-lookup"><span data-stu-id="3bf29-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>

  <span data-ttu-id="3bf29-126">Wyjątek polega na tym, że `TypeDef` obiekt może mieć przyrostowe składowe oflagowane jako `mdPrivateScope` .</span><span class="sxs-lookup"><span data-stu-id="3bf29-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="3bf29-127">Po napotkaniu te elementy `MergeEnd` przyrostowo dodaje je do bieżącego zakresu bez względu na duplikaty.</span><span class="sxs-lookup"><span data-stu-id="3bf29-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="3bf29-128">Ponieważ kompilator rozumie zakres prywatny, kompilator musi być odpowiedzialny za Wymuszanie reguł.</span><span class="sxs-lookup"><span data-stu-id="3bf29-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>

- <span data-ttu-id="3bf29-129">Względne adresy wirtualne (RVA) nie są importowane ani scalone; Kompilator powinien reemitować te informacje.</span><span class="sxs-lookup"><span data-stu-id="3bf29-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>

- <span data-ttu-id="3bf29-130">Atrybuty niestandardowe są scalane tylko wtedy, gdy element, do którego są dołączone, zostanie scalony.</span><span class="sxs-lookup"><span data-stu-id="3bf29-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="3bf29-131">Na przykład atrybuty niestandardowe skojarzone z klasą są scalane podczas pierwszego napotkania klasy.</span><span class="sxs-lookup"><span data-stu-id="3bf29-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="3bf29-132">Jeśli atrybuty niestandardowe są skojarzone z `TypeDef` lub `MemberDef` , które są specyficzne dla jednostki kompilacji (na przykład sygnatury czasowej kompilowania elementu członkowskiego), nie są scalone i do kompilatora można usunąć lub zaktualizować takie metadane.</span><span class="sxs-lookup"><span data-stu-id="3bf29-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="3bf29-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bf29-133">Requirements</span></span>

<span data-ttu-id="3bf29-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bf29-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3bf29-135">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3bf29-135">**Header:** Cor.h</span></span>

<span data-ttu-id="3bf29-136">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3bf29-136">**Library:** Used as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="3bf29-137">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf29-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3bf29-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bf29-138">See also</span></span>

- [<span data-ttu-id="3bf29-139">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bf29-139">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3bf29-140">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3bf29-140">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
