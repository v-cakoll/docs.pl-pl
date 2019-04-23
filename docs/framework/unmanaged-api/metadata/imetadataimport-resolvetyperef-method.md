---
title: IMetaDataImport::ResolveTypeRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f929e6b338d4fd48b2a6ef9588523377e0dd8faa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096065"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="618c5-102">IMetaDataImport::ResolveTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="618c5-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="618c5-103">Rozpoznaje <xref:System.Type> reprezentowany przez określony token TypeRef odwołania.</span><span class="sxs-lookup"><span data-stu-id="618c5-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="618c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="618c5-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="618c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="618c5-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="618c5-106">[in] Token TypeRef metadanych do zwrócenia informacji o typie odwołania.</span><span class="sxs-lookup"><span data-stu-id="618c5-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="618c5-107">[in] IID interfejsu do zwrócenia w `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="618c5-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="618c5-108">Zazwyczaj powinien to być IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="618c5-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="618c5-109">[out] Interfejs do zakresu modułu, w którym zdefiniowano typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="618c5-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="618c5-110">[out] Wskaźnik do TypeDef token, który reprezentuje typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="618c5-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="618c5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="618c5-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="618c5-112">Nie należy używać tej metody, jeśli wiele domen aplikacji są ładowane.</span><span class="sxs-lookup"><span data-stu-id="618c5-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="618c5-113">Metoda respektują granice domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="618c5-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="618c5-114">Jeśli wiele wersji zestawu zostaną załadowane i zawierają ten sam typ o tej samej przestrzeni nazw, metoda zwraca zakres modułu pierwszego typu, które znajdzie.</span><span class="sxs-lookup"><span data-stu-id="618c5-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="618c5-115">`ResolveTypeRef` Metoda wyszukiwania dla definicji typu w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="618c5-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="618c5-116">Jeśli zostanie znaleziony w definicji typu, `ResolveTypeRef` zwraca interfejs do tego zakresu modułu, a także token element TypeDef dla typu.</span><span class="sxs-lookup"><span data-stu-id="618c5-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="618c5-117">Jeśli odniesienie typu, które mają zostać rozwiązane, ma zakres rozpoznawania elementu AssemblyRef, `ResolveTypeRef` metoda szuka dopasowania tylko w przypadku zakresów metadanych, które już zostały otwarte przy użyciu wywołań albo [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)metody lub [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="618c5-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="618c5-118">Jest to spowodowane `ResolveTypeRef` nie może ustalić z tylko zakres elementu AssemblyRef miejsce na dysku lub w globalnej pamięci podręcznej zestawu przechowywania.</span><span class="sxs-lookup"><span data-stu-id="618c5-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="618c5-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="618c5-119">Requirements</span></span>  
 <span data-ttu-id="618c5-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="618c5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="618c5-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="618c5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="618c5-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="618c5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="618c5-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="618c5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="618c5-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="618c5-124">See also</span></span>

- [<span data-ttu-id="618c5-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="618c5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="618c5-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="618c5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
