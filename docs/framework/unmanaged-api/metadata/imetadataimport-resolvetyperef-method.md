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
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951877"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="411c6-102">IMetaDataImport::ResolveTypeRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="411c6-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="411c6-103"><xref:System.Type> Rozwiązuje odwołanie reprezentowane przez określony token elementu TypeRef.</span><span class="sxs-lookup"><span data-stu-id="411c6-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="411c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="411c6-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="411c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="411c6-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="411c6-106">podczas Token metadanych elementu TypeRef, który ma zwracać informacje o typie, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="411c6-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="411c6-107">podczas Identyfikator IID interfejsu do zwrócenia `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="411c6-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="411c6-108">Zwykle jest to IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="411c6-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="411c6-109">określoną Interfejs do zakresu modułu, w którym jest zdefiniowany typ, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="411c6-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="411c6-110">określoną Wskaźnik do tokenu TypeDef, który reprezentuje przywoływany typ.</span><span class="sxs-lookup"><span data-stu-id="411c6-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="411c6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="411c6-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="411c6-112">Nie należy używać tej metody w przypadku ładowania wielu domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="411c6-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="411c6-113">Metoda nie uwzględnia granic domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="411c6-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="411c6-114">Jeśli wiele wersji zestawu jest załadowanych i zawierają ten sam typ z tą samą przestrzenią nazw, metoda zwraca zakres modułu pierwszego znalezionego typu.</span><span class="sxs-lookup"><span data-stu-id="411c6-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="411c6-115">`ResolveTypeRef` Metoda wyszukuje definicję typu w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="411c6-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="411c6-116">Jeśli zostanie znaleziona definicja typu, `ResolveTypeRef` zwraca interfejs do tego zakresu modułu, a także token typedef dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="411c6-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="411c6-117">Jeśli odwołanie do typu, które ma zostać rozpoznane, ma zakres rozwiązań elementu AssemblyRef `ResolveTypeRef` , Metoda wyszukuje dopasowanie tylko w zakresach metadanych, które zostały już otwarte z wywołaniami metody [IMetaDataDispenser:: OpenScope —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) lub [ IMetaDataDispenser:: OpenScopeOnMemory —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) , metoda.</span><span class="sxs-lookup"><span data-stu-id="411c6-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="411c6-118">Wynika to z `ResolveTypeRef` faktu, że program nie może ustalić tylko zakresu elementu AssemblyRef, gdzie na dysku lub w pamięci podręcznej zestawów globalnych jest przechowywany zestaw.</span><span class="sxs-lookup"><span data-stu-id="411c6-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="411c6-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="411c6-119">Requirements</span></span>  
 <span data-ttu-id="411c6-120">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="411c6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="411c6-121">**Nagłówki** Cor. h</span><span class="sxs-lookup"><span data-stu-id="411c6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="411c6-122">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="411c6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="411c6-123">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="411c6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411c6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="411c6-124">See also</span></span>

- [<span data-ttu-id="411c6-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="411c6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="411c6-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="411c6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
