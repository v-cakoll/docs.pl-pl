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
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177283"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="bf858-102">IMetaDataImport::FindMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf858-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="bf858-103">Pobiera wskaźnik do MemberDef token dla pola lub metody, <xref:System.Type> która jest ujęta przez określony i który ma określoną nazwę i podpis metadanych.</span><span class="sxs-lookup"><span data-stu-id="bf858-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf858-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf858-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf858-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf858-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="bf858-106">[w] TypeDef token dla klasy lub interfejsu, który otacza element członkowski do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="bf858-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="bf858-107">Jeśli ta `mdTokenNil`wartość jest , wyszukiwanie jest wykonywane dla zmiennej globalnej lub funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="bf858-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="bf858-108">[w] Nazwa członka do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="bf858-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="bf858-109">[w] Wskaźnik do podpisu binarnych metadanych członka.</span><span class="sxs-lookup"><span data-stu-id="bf858-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="bf858-110">[w] Rozmiar w bajtach . `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="bf858-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="bf858-111">[na zewnątrz] Wskaźnik do pasującego tokenu MemberDef.</span><span class="sxs-lookup"><span data-stu-id="bf858-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf858-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf858-112">Remarks</span></span>  
 <span data-ttu-id="bf858-113">Element członkowski można określić za`td`pomocą otaczającej`szName`go klasy lub`pvSigBlob`interfejsu ( ), jego nazwy ( i opcjonalnie jego podpisu ( ).</span><span class="sxs-lookup"><span data-stu-id="bf858-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="bf858-114">Może istnieć wiele elementów członkowskich o tej samej nazwie w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="bf858-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="bf858-115">W takim przypadku przekaż podpis członka, aby znaleźć unikatowe dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="bf858-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="bf858-116">Podpis przekazany `FindMember` do musi zostały wygenerowane w bieżącym zakresie, ponieważ podpisy są powiązane z określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="bf858-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="bf858-117">Podpis można osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="bf858-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="bf858-118">Token jest indeksem do lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="bf858-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="bf858-119">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu `FindMember`i użyć tego podpisu jako danych wejściowych do .</span><span class="sxs-lookup"><span data-stu-id="bf858-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="bf858-120">`FindMember`znajduje tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje odziedziczonych członków.</span><span class="sxs-lookup"><span data-stu-id="bf858-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf858-121">`FindMember`jest metodą pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="bf858-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="bf858-122">Wywołuje [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); jeśli to wywołanie nie `FindMember` znajdzie dopasowania, wywoła [iMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf858-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf858-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf858-123">Requirements</span></span>  
 <span data-ttu-id="bf858-124">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf858-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf858-125">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf858-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf858-126">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf858-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf858-127">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf858-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf858-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf858-128">See also</span></span>

- [<span data-ttu-id="bf858-129">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf858-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bf858-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf858-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
