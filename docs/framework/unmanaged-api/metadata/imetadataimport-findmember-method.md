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
ms.openlocfilehash: 4eefb7ec1e7d0d130ec64531a59d1d5bbce04963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968923"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="039c1-102">IMetaDataImport::FindMember — Metoda</span><span class="sxs-lookup"><span data-stu-id="039c1-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="039c1-103">Pobiera wskaźnik do tokenu MemberDef dla pola lub metody, która jest ujęta w określony <xref:System.Type> i który ma określoną nazwę i sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="039c1-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="039c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="039c1-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="039c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="039c1-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="039c1-106">podczas Token TypeDef dla klasy lub interfejsu, który obejmuje element członkowski do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="039c1-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="039c1-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane dla zmiennej globalnej lub funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="039c1-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="039c1-108">podczas Nazwa elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="039c1-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="039c1-109">podczas Wskaźnik do binarnego podpisu metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="039c1-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="039c1-110">podczas Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="039c1-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="039c1-111">określoną Wskaźnik do zgodnego tokenu MemberDef.</span><span class="sxs-lookup"><span data-stu-id="039c1-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="039c1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="039c1-112">Remarks</span></span>  
 <span data-ttu-id="039c1-113">Należy określić składową przy użyciu jej klasy lub interfejsu (`td`), jej nazwy (`szName`) i opcjonalnie jej sygnatury (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="039c1-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="039c1-114">Może istnieć wiele elementów członkowskich o tej samej nazwie w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="039c1-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="039c1-115">W takim przypadku Przekaż podpis elementu członkowskiego, aby znaleźć unikatowe dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="039c1-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="039c1-116">Sygnatura przekazano `FindMember` do musi być wygenerowana w bieżącym zakresie, ponieważ sygnatury są powiązane z konkretnym zakresem.</span><span class="sxs-lookup"><span data-stu-id="039c1-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="039c1-117">Podpis może osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="039c1-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="039c1-118">Token jest indeksem tabeli lokalnych TypeDef.</span><span class="sxs-lookup"><span data-stu-id="039c1-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="039c1-119">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu i użyć tej sygnatury jako danych wejściowych `FindMember`do.</span><span class="sxs-lookup"><span data-stu-id="039c1-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="039c1-120">`FindMember`znajduje tylko elementy członkowskie, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="039c1-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="039c1-121">`FindMember`jest metodą pomocnika.</span><span class="sxs-lookup"><span data-stu-id="039c1-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="039c1-122">Wywołuje [IMetaDataImport:: FindMethod —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Jeśli to wywołanie nie znajdzie dopasowania, `FindMember` wówczas wywołuje [IMetaDataImport:: FindField —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="039c1-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="039c1-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="039c1-123">Requirements</span></span>  
 <span data-ttu-id="039c1-124">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="039c1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="039c1-125">**Nagłówki** Cor. h</span><span class="sxs-lookup"><span data-stu-id="039c1-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="039c1-126">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="039c1-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="039c1-127">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="039c1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039c1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="039c1-128">See also</span></span>

- [<span data-ttu-id="039c1-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="039c1-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="039c1-130">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="039c1-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
