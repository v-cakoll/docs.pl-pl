---
title: "IMetaDataImport::FindMember — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a20930688aed210309a719de2c7187f1f5fd1f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="53867-102">IMetaDataImport::FindMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="53867-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="53867-103">Pobiera wskaźnik do MemberDef token dla pola lub metody, która jest zawarta w określonym <xref:System.Type> z określoną sygnaturą nazwy i metadanych.</span><span class="sxs-lookup"><span data-stu-id="53867-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53867-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53867-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53867-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53867-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="53867-106">[in] Token TypeDef dla klasy lub interfejsu, który dodaje element do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="53867-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="53867-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmiennej globalnej lub globalnego funkcji.</span><span class="sxs-lookup"><span data-stu-id="53867-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="53867-108">[in] Nazwa elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="53867-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="53867-109">[in] Wskaźnik do sygnatury binarne metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="53867-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="53867-110">[in] Wyrażony w bajtach rozmiar `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="53867-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="53867-111">[out] Wskaźnik do dopasowania tokenu MemberDef.</span><span class="sxs-lookup"><span data-stu-id="53867-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53867-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53867-112">Remarks</span></span>  
 <span data-ttu-id="53867-113">Określ element członkowski za pomocą jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="53867-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="53867-114">Może to być wielu członków o tej samej nazwie w klasie lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="53867-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="53867-115">W takim przypadku należy przekazać podpisu elementu członkowskiego można znaleźć unikatowego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="53867-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="53867-116">Podpis przekazany do `FindMember` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="53867-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="53867-117">Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="53867-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="53867-118">Token jest indeks do lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="53867-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="53867-119">Nie można skompilować podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używania jako danych wejściowych do danych wejściowych do tego podpisu `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="53867-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="53867-120">`FindMember`Wyszukuje tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasy lub interfejsu; dziedziczone elementy członkowskie nie zostanie znaleziona.</span><span class="sxs-lookup"><span data-stu-id="53867-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53867-121">`FindMember`jest to metoda pomocnika.</span><span class="sxs-lookup"><span data-stu-id="53867-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="53867-122">Wywołuje [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Jeśli tego wywołania nie znaleziono dopasowania, `FindMember` następnie wywołuje [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="53867-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53867-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53867-123">Requirements</span></span>  
 <span data-ttu-id="53867-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53867-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53867-125">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53867-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53867-126">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53867-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53867-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53867-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53867-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53867-128">See Also</span></span>  
 [<span data-ttu-id="53867-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="53867-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="53867-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="53867-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
