---
title: IMetaDataEmit::DefineImportMember — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 341972629e18213536919fe53bfae94613b4d6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777645"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="c4db9-102">IMetaDataEmit::DefineImportMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4db9-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="c4db9-103">Tworzy odwołanie do określonego elementu członkowskiego typu lub moduł, który jest zdefiniowane poza bieżącym zakresie i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="c4db9-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4db9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4db9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4db9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4db9-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="c4db9-106">[in] [Imetadataassemblyimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejs, który reprezentuje zestaw, z którego docelowy element członkowski jest importowany.</span><span class="sxs-lookup"><span data-stu-id="c4db9-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c4db9-107">[in] Tablica, która zawiera wartość skrótu dla zestawu określonego przez `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="c4db9-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c4db9-108">[in] Liczba bajtów w `pbHashValue` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4db9-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="c4db9-109">[in] [Imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs, który reprezentuje zakres metadanych, z którego docelowy element członkowski jest importowany.</span><span class="sxs-lookup"><span data-stu-id="c4db9-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="c4db9-110">[in] Token metadanych, który określa docelowy element członkowski.</span><span class="sxs-lookup"><span data-stu-id="c4db9-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="c4db9-111">Token może być `mdMethodDef` (w przypadku elementu członkowskiego metody) `mdProperty` (w przypadku właściwości elementu członkowskiego), lub `mdFieldDef` (dla pola elementu członkowskiego) tokenu.</span><span class="sxs-lookup"><span data-stu-id="c4db9-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="c4db9-112">[in] [Imetadataassemblyemit —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interfejs, który reprezentuje zestaw, do którego docelowy element członkowski jest importowany.</span><span class="sxs-lookup"><span data-stu-id="c4db9-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="c4db9-113">[in] `mdTypeRef` Lub `mdModuleRef` tokenu dla typu lub modułu, odpowiednio, który jest właścicielem docelowy element członkowski.</span><span class="sxs-lookup"><span data-stu-id="c4db9-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="c4db9-114">[out] `mdMemberRef` Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c4db9-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4db9-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4db9-115">Remarks</span></span>  
 <span data-ttu-id="c4db9-116">`DefineImportMember` Metoda wyszukuje element określony przez `mbMember`, która jest zdefiniowana w innym zakresie określonym przez `pImport`i pobiera jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4db9-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="c4db9-117">Używa tych informacji w celu wywołania [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody w bieżącym zakresie można utworzyć odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c4db9-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="c4db9-118">Ogólnie rzecz biorąc, zanim użyjesz `DefineImportMember` metody, należy utworzyć, w bieżącym zakresie, odwołanie do typu lub odwołania do modułu docelowy element członkowski klasy nadrzędnej, interfejs lub moduł.</span><span class="sxs-lookup"><span data-stu-id="c4db9-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="c4db9-119">Token metadanych dla tego odwołania jest następnie przekazywany w `tkParent` argumentu.</span><span class="sxs-lookup"><span data-stu-id="c4db9-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="c4db9-120">Nie trzeba utworzyć odwołanie do elementu nadrzędnego elementu członkowskiego docelowy, jeśli będzie można rozwiązać w dalszej części, kompilator lub konsolidator.</span><span class="sxs-lookup"><span data-stu-id="c4db9-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="c4db9-121">Podsumowując:</span><span class="sxs-lookup"><span data-stu-id="c4db9-121">To summarize:</span></span>  
  
- <span data-ttu-id="c4db9-122">Jeśli docelowy element członkowski jest ona polem ani metodą, użyj jednej [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodę, aby utworzyć odwołanie do typu, w bieżącym zakresie dla klasy nadrzędnej lub interfejs nadrzędny tego elementu.</span><span class="sxs-lookup"><span data-stu-id="c4db9-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="c4db9-123">Jeśli docelowy element członkowski, zmienna lub globalnego funkcją globalną (czyli nie jest członkiem klasy lub interfejsu), użyj [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodę w celu utworzenia odwołania do modułu w bieżącym zakresie i dla nadrzędnego elementu członkowskiego Moduł.</span><span class="sxs-lookup"><span data-stu-id="c4db9-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="c4db9-124">Jeśli nadrzędny docelowy element członkowski zostanie rozwiązany później przez kompilator lub konsolidator, należy przekazać `mdTokenNil` w `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="c4db9-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="c4db9-125">Jest jedyny scenariusz, w którym ma to zastosowanie, gdy funkcja globalna lub zmienna globalna jest importowany z pliku .obj, który ostatecznie zostanie połączony do bieżącego modułu i metadane, scalone.</span><span class="sxs-lookup"><span data-stu-id="c4db9-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4db9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4db9-126">Requirements</span></span>  
 <span data-ttu-id="c4db9-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4db9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4db9-128">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c4db9-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4db9-129">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4db9-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4db9-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4db9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4db9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4db9-131">See also</span></span>

- [<span data-ttu-id="c4db9-132">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4db9-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c4db9-133">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4db9-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
