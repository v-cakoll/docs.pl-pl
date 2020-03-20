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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175866"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="ac329-102">IMetaDataEmit::DefineImportMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac329-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="ac329-103">Tworzy odwołanie do określonego elementu członkowskiego typu lub modułu, który jest zdefiniowany poza bieżącym zakresem i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="ac329-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac329-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac329-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ac329-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac329-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="ac329-106">[w] [Interfejs IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) który reprezentuje zestaw, z którego jest importowany element członkowski obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ac329-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ac329-107">[w] Tablica zawierająca skrót dla zestawu `pAssemImport`określonego przez program .</span><span class="sxs-lookup"><span data-stu-id="ac329-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ac329-108">[w] Liczba bajtów w `pbHashValue` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ac329-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="ac329-109">[w] Interfejs [IMetaDataImport reprezentujący](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) zakres metadanych, z którego jest importowany element członkowski obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ac329-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="ac329-110">[w] Token metadanych, który określa docelowy element członkowski.</span><span class="sxs-lookup"><span data-stu-id="ac329-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="ac329-111">Token może być `mdMethodDef` tokenem (dla `mdProperty` metody elementu członkowskiego) `mdFieldDef` (dla właściwości elementu członkowskiego) lub (dla pola członkowskiego).</span><span class="sxs-lookup"><span data-stu-id="ac329-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="ac329-112">[w] [Interfejs IMetaDataAssemblyEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) który reprezentuje zestaw, do którego importowany jest element docelowy.</span><span class="sxs-lookup"><span data-stu-id="ac329-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="ac329-113">[w] Lub `mdTypeRef` `mdModuleRef` token dla typu lub modułu, odpowiednio, który jest właścicielem elementu członkowskiego docelowego.</span><span class="sxs-lookup"><span data-stu-id="ac329-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="ac329-114">[na zewnątrz] Token, `mdMemberRef` który jest zdefiniowany w bieżącym zakresie odwołania elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ac329-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac329-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac329-115">Remarks</span></span>  
 <span data-ttu-id="ac329-116">Metoda `DefineImportMember` wyszukuje element `mbMember`członkowski, określony przez , `pImport`który jest zdefiniowany w innym zakresie, określonym przez program , i pobiera jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac329-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="ac329-117">Używa tych informacji do wywołania [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody w bieżącym zakresie, aby utworzyć odwołanie do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ac329-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="ac329-118">Ogólnie rzecz biorąc przed `DefineImportMember` użyciem metody, należy utworzyć w bieżącym zakresie odwołanie do typu lub odwołanie do modułu dla docelowego elementu nadrzędnego klasy, interfejsu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="ac329-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="ac329-119">Token metadanych dla tego odwołania `tkParent` jest następnie przekazywany w argumie.</span><span class="sxs-lookup"><span data-stu-id="ac329-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="ac329-120">Nie trzeba tworzyć odwołanie do elementu nadrzędnego elementu docelowego, jeśli zostanie rozwiązany później przez kompilator lub konsolidator.</span><span class="sxs-lookup"><span data-stu-id="ac329-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="ac329-121">Podsumowując:</span><span class="sxs-lookup"><span data-stu-id="ac329-121">To summarize:</span></span>  
  
- <span data-ttu-id="ac329-122">Jeśli element członkowski obiektu docelowego jest polem lub metodą, należy użyć [metody IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [metody IMetaDataEmit::DefineImportType,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ac329-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="ac329-123">Jeśli element członkowski obiektu docelowego jest zmienną globalną lub funkcją globalną (czyli nie jest członkiem klasy lub interfejsu), użyj metody [IMetaDataEmit::DefineModuleRef,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) aby utworzyć odwołanie do modułu w bieżącym zakresie dla modułu nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ac329-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="ac329-124">Jeśli element nadrzędny elementu docelowego zostanie później rozwiązany przez kompilator lub konsolidator, a następnie przekaż `mdTokenNil` . `tkParent`</span><span class="sxs-lookup"><span data-stu-id="ac329-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="ac329-125">Jedynym scenariuszem, w którym ma to zastosowanie, jest, gdy funkcja globalna lub zmienna globalna jest importowana z pliku obj, który ostatecznie zostanie połączony z bieżącym modułem i scalonymi metadanymi.</span><span class="sxs-lookup"><span data-stu-id="ac329-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac329-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac329-126">Requirements</span></span>  
 <span data-ttu-id="ac329-127">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac329-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac329-128">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac329-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac329-129">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac329-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac329-130">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac329-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac329-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac329-131">See also</span></span>

- [<span data-ttu-id="ac329-132">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ac329-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ac329-133">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac329-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
