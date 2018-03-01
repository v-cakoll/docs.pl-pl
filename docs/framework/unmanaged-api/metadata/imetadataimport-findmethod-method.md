---
title: "IMetaDataImport::FindMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e59cc440ba004545c31d6b25d36cca4fdfb58899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="89954-102">IMetaDataImport::FindMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="89954-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="89954-103">Pobiera wskaźnik do elementu MethodDef token metodę, która jest zawarta w określonym <xref:System.Type> z określoną sygnaturą nazwy i metadanych.</span><span class="sxs-lookup"><span data-stu-id="89954-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89954-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89954-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89954-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89954-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="89954-106">[in] `mdTypeDef` Tokenu dla typu (klasy lub interfejsu) ograniczający element członkowski do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="89954-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="89954-107">Jeśli ta wartość jest `mdTokenNil`, a następnie wyszukiwanie jest wykonywane na potrzeby funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="89954-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="89954-108">[in] Nazwa metody do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="89954-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="89954-109">[in] Wskaźnik do metadanych binarne sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="89954-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="89954-110">[in] Wyrażony w bajtach rozmiar `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="89954-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="89954-111">[out] Wskaźnik do dopasowania tokenu MethodDef.</span><span class="sxs-lookup"><span data-stu-id="89954-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89954-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89954-112">Remarks</span></span>  
 <span data-ttu-id="89954-113">Określ metodę, za pomocą jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="89954-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="89954-114">Może istnieć wiele metod o tej samej nazwie w klasie lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="89954-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="89954-115">W takim przypadku należy przekazać podpis metody można znaleźć unikatowego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="89954-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="89954-116">Podpis przekazany do `FindMethod` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="89954-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="89954-117">Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="89954-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="89954-118">Token jest indeks do lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="89954-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="89954-119">Nie można skompilować podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używania jako danych wejściowych do danych wejściowych do tego podpisu `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="89954-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="89954-120">`FindMethod`znajduje tylko metody, które zostały zdefiniowane bezpośrednio w klasy lub interfejsu; nie odnajdzie dziedziczonej metody.</span><span class="sxs-lookup"><span data-stu-id="89954-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89954-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89954-121">Requirements</span></span>  
 <span data-ttu-id="89954-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89954-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89954-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="89954-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89954-124">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89954-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89954-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89954-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89954-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89954-126">See Also</span></span>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="89954-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="89954-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="89954-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="89954-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
