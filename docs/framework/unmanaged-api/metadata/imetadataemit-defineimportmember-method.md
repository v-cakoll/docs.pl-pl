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
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431856"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="efe92-102">IMetaDataEmit::DefineImportMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="efe92-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="efe92-103">Tworzy odwołanie do określonego elementu członkowskiego typu lub modułu, który jest zdefiniowany poza bieżącym zakresem, i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="efe92-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe92-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efe92-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="efe92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efe92-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="efe92-106">podczas Interfejs [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , który reprezentuje zestaw, z którego zostanie zaimportowany członek docelowy.</span><span class="sxs-lookup"><span data-stu-id="efe92-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="efe92-107">podczas Tablica, która zawiera skrót dla zestawu określonego przez `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="efe92-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="efe92-108">podczas Liczba bajtów w tablicy `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="efe92-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="efe92-109">podczas Interfejs [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) reprezentujący zakres metadanych, z którego zaimportowano element docelowy.</span><span class="sxs-lookup"><span data-stu-id="efe92-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="efe92-110">podczas Token metadanych określający docelowy element członkowski.</span><span class="sxs-lookup"><span data-stu-id="efe92-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="efe92-111">Token może być `mdMethodDef` (dla metody członkowskiej), `mdProperty` (dla właściwości elementu członkowskiego) lub `mdFieldDef` (dla pola elementu członkowskiego).</span><span class="sxs-lookup"><span data-stu-id="efe92-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="efe92-112">podczas Interfejs [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) , który reprezentuje zestaw, do którego zaimportowany jest docelowy element członkowski.</span><span class="sxs-lookup"><span data-stu-id="efe92-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="efe92-113">podczas Token `mdTypeRef` lub `mdModuleRef` dla typu lub modułu, który jest właścicielem docelowego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="efe92-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="efe92-114">określoną Token `mdMemberRef`, który jest zdefiniowany w bieżącym zakresie dla odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="efe92-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efe92-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efe92-115">Remarks</span></span>  
 <span data-ttu-id="efe92-116">Metoda `DefineImportMember` wyszukuje element członkowski, określony przez `mbMember`, który jest zdefiniowany w innym zakresie, określonym przez `pImport`i pobiera jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="efe92-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="efe92-117">Używa tych informacji do wywołania metody [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) w bieżącym zakresie w celu utworzenia odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="efe92-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="efe92-118">Ogólnie rzecz biorąc, przed użyciem metody `DefineImportMember` należy utworzyć, w bieżącym zakresie, odwołanie do typu lub odwołanie do modułu dla klasy nadrzędnej, interfejsu lub modułu członkowskiego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="efe92-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="efe92-119">Token metadanych dla tego odwołania jest następnie przesyłany w `tkParent` argument.</span><span class="sxs-lookup"><span data-stu-id="efe92-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="efe92-120">Nie trzeba tworzyć odwołania do elementu nadrzędnego elementu członkowskiego docelowej, jeśli zostanie on rozwiązany później przez kompilator lub konsolidator.</span><span class="sxs-lookup"><span data-stu-id="efe92-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="efe92-121">Aby podsumować:</span><span class="sxs-lookup"><span data-stu-id="efe92-121">To summarize:</span></span>  
  
- <span data-ttu-id="efe92-122">Jeśli docelowa składowa jest polem lub metodą, użyj metody [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) , aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="efe92-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="efe92-123">Jeśli element członkowski docelowa to zmienna globalna lub funkcja globalna (to nie jest element członkowski klasy lub interfejsu), użyj metody [IMetaDataEmit::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) , aby utworzyć odwołanie do modułu w bieżącym zakresie dla modułu nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="efe92-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="efe92-124">Jeśli element nadrzędny elementu członkowskiego docelowej zostanie rozwiązany później przez kompilator lub konsolidator, Przekaż `mdTokenNil` w `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="efe92-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="efe92-125">Jedyny scenariusz, w którym dotyczy to, gdy globalna funkcja lub zmienna globalna jest importowana z pliku. obj, który ostatecznie zostanie połączony z bieżącym modułem i scalone metadane.</span><span class="sxs-lookup"><span data-stu-id="efe92-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe92-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efe92-126">Requirements</span></span>  
 <span data-ttu-id="efe92-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efe92-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efe92-128">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="efe92-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efe92-129">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efe92-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efe92-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efe92-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe92-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efe92-131">See also</span></span>

- [<span data-ttu-id="efe92-132">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="efe92-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="efe92-133">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="efe92-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
