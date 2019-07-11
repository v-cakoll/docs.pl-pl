---
title: IMetaDataImport::FindMember — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caec760cea52cb14d3fdb5d4cf0b59adcae5633b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782516"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="b2e97-102">IMetaDataImport::FindMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2e97-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="b2e97-103">Pobiera wskaźnik do MemberDef tokenu dla pola lub metody, która jest ujęta w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.</span><span class="sxs-lookup"><span data-stu-id="b2e97-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2e97-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2e97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2e97-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b2e97-106">[in] Token element TypeDef dla klasy lub interfejsu, który otacza elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="b2e97-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="b2e97-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane dla zmiennej globalnej lub globalnego funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2e97-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b2e97-108">[in] Nazwa elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="b2e97-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b2e97-109">[in] Wskaźnik do podpisu binarne metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b2e97-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b2e97-110">[in] Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b2e97-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b2e97-111">[out] Wskaźnik do zgodnego tokenu MemberDef.</span><span class="sxs-lookup"><span data-stu-id="b2e97-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2e97-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2e97-112">Remarks</span></span>  
 <span data-ttu-id="b2e97-113">Określ element członkowski przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="b2e97-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="b2e97-114">Może istnieć wiele składowych o tej samej nazwie w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="b2e97-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="b2e97-115">W takim przypadku należy przekazać podpisu elementu członkowskiego, aby znaleźć unikatowego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="b2e97-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="b2e97-116">Podpis jest przekazywany do `FindMember` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="b2e97-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b2e97-117">Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="b2e97-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b2e97-118">Token jest to indeks w lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b2e97-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="b2e97-119">Nie można tworzyć sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i za ten podpis jako dane wejściowe do wprowadzania `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="b2e97-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="b2e97-120">`FindMember` Umożliwia znalezienie tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasę lub interfejs; dziedziczone elementy członkowskie nie zostanie znaleziona.</span><span class="sxs-lookup"><span data-stu-id="b2e97-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2e97-121">`FindMember` jest metodą pomocnika.</span><span class="sxs-lookup"><span data-stu-id="b2e97-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="b2e97-122">Wywołuje [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Jeśli jest to wywołanie nie znajdzie dopasowania `FindMember` następnie wywołuje [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="b2e97-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e97-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2e97-123">Requirements</span></span>  
 <span data-ttu-id="b2e97-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2e97-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2e97-125">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b2e97-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2e97-126">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2e97-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2e97-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2e97-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e97-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2e97-128">See also</span></span>

- [<span data-ttu-id="b2e97-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2e97-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b2e97-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2e97-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
