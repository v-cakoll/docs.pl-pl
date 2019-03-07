---
title: IMetaDataImport::FindMemberRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a58cba0ce4672a479cf5af9467d024a1b1562fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474296"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="a8eef-102">IMetaDataImport::FindMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8eef-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="a8eef-103">Pobiera wskaźnik do elementu członkowskiego tokenu MemberRef odwołanie to znaczy ujętego w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.</span><span class="sxs-lookup"><span data-stu-id="a8eef-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8eef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8eef-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8eef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8eef-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a8eef-106">[in] Token TypeRef dla klasy lub interfejsu, który zawiera odwołania do składowej do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="a8eef-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="a8eef-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmienną globalną lub odwołanie do globalnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a8eef-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="a8eef-108">[in] Nazwa odwołania do składowej do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="a8eef-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a8eef-109">[in] Wskaźnik do podpisu metadanych binarne odwołania do składowej.</span><span class="sxs-lookup"><span data-stu-id="a8eef-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a8eef-110">[in] Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a8eef-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="a8eef-111">[out] Wskaźnik do zgodnego tokenu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="a8eef-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8eef-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8eef-112">Remarks</span></span>  
 <span data-ttu-id="a8eef-113">Określ element członkowski przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="a8eef-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="a8eef-114">Podpis jest przekazywany do `FindMemberRef` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="a8eef-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="a8eef-115">Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="a8eef-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="a8eef-116">Token jest to indeks w lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a8eef-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="a8eef-117">Nie można tworzenia sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i używać tego podpisu jako dane wejściowe `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="a8eef-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="a8eef-118">`FindMemberRef` Umożliwia znalezienie tylko odwołania do elementu członkowskiego, które zostały zdefiniowane bezpośrednio w klasę lub interfejs; nie odnajdzie odwołania dziedziczonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a8eef-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8eef-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8eef-119">Requirements</span></span>  
 <span data-ttu-id="a8eef-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8eef-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8eef-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a8eef-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8eef-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8eef-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8eef-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8eef-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8eef-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8eef-124">See also</span></span>
- [<span data-ttu-id="a8eef-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8eef-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a8eef-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8eef-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
