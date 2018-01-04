---
title: "IMetaDataImport::FindMemberRef — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMemberRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a94fb09e1ff62abac9dd716257ba75542453707e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="9cc72-102">IMetaDataImport::FindMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cc72-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="9cc72-103">Pobiera wskaźnik do elementu członkowskiego tokenu MemberRef oznacza to odwołanie ujęty w określonym <xref:System.Type> z określoną sygnaturą nazwy i metadanych.</span><span class="sxs-lookup"><span data-stu-id="9cc72-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cc72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cc72-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cc72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cc72-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="9cc72-106">[in] Token TypeRef dla klasy lub interfejsu, który umieszcza odwołanie do elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="9cc72-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="9cc72-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmiennej globalnej lub odwołanie do funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="9cc72-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="9cc72-108">[in] Nazwa odwołania do elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="9cc72-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9cc72-109">[in] Wskaźnik do sygnatury binarne metadanych odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9cc72-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9cc72-110">[in] Wyrażony w bajtach rozmiar `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9cc72-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="9cc72-111">[out] Wskaźnik do dopasowania tokenu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="9cc72-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cc72-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cc72-112">Remarks</span></span>  
 <span data-ttu-id="9cc72-113">Określ element członkowski za pomocą jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="9cc72-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="9cc72-114">Podpis przekazany do `FindMemberRef` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="9cc72-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="9cc72-115">Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="9cc72-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="9cc72-116">Token jest indeks do lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="9cc72-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="9cc72-117">Nie kompilacji podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używają tego podpisu jako dane wejściowe `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="9cc72-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="9cc72-118">`FindMemberRef`Wyszukuje tylko odwołania do elementu członkowskiego zdefiniowane bezpośrednio w klasy lub interfejsu; dziedziczony element członkowski odwołania nie zostanie znaleziona.</span><span class="sxs-lookup"><span data-stu-id="9cc72-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cc72-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cc72-119">Requirements</span></span>  
 <span data-ttu-id="9cc72-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cc72-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cc72-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9cc72-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cc72-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9cc72-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9cc72-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cc72-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc72-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cc72-124">See Also</span></span>  
 [<span data-ttu-id="9cc72-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cc72-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9cc72-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cc72-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
