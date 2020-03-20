---
title: IMetaDataImport::FindMethod — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177248"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="e7e9b-102">IMetaDataImport::FindMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7e9b-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="e7e9b-103">Pobiera wskaźnik do MethodDef token dla metody, która <xref:System.Type> jest ujęta przez określony i który ma określoną nazwę i podpis metadanych.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7e9b-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7e9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7e9b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e7e9b-106">[w] Token `mdTypeDef` dla typu (klasy lub interfejsu), który otacza element członkowski do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="e7e9b-107">Jeśli ta `mdTokenNil`wartość jest , a następnie wyszukiwanie jest wykonywane dla funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="e7e9b-108">[w] Nazwa metody wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e7e9b-109">[w] Wskaźnik do podpisu binarnych metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e7e9b-110">[w] Rozmiar w bajtach . `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="e7e9b-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="e7e9b-111">[na zewnątrz] Wskaźnik do pasującego tokenu MethodDef.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7e9b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7e9b-112">Remarks</span></span>  
 <span data-ttu-id="e7e9b-113">Metodę można określić przy użyciu otaczającej jej klasy lub interfejsu (`td`), jej nazwy (`szName`i opcjonalnie jej podpisu (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="e7e9b-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="e7e9b-114">Może istnieć wiele metod o tej samej nazwie w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="e7e9b-115">W takim przypadku należy przekazać podpis metody, aby znaleźć unikatowe dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="e7e9b-116">Podpis przekazany `FindMethod` do musi zostały wygenerowane w bieżącym zakresie, ponieważ podpisy są powiązane z określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="e7e9b-117">Podpis można osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="e7e9b-118">Token jest indeksem do lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="e7e9b-119">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu `FindMethod`i użyć tego podpisu jako danych wejściowych do .</span><span class="sxs-lookup"><span data-stu-id="e7e9b-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="e7e9b-120">`FindMethod`znajduje tylko metody, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje metod dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="e7e9b-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7e9b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7e9b-121">Requirements</span></span>  
 <span data-ttu-id="e7e9b-122">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e9b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e9b-123">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7e9b-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7e9b-124">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7e9b-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7e9b-125">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7e9b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e9b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7e9b-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="e7e9b-127">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e7e9b-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e7e9b-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7e9b-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
