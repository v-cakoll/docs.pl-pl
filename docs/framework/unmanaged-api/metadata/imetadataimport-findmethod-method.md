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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164804"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="93dc0-102">IMetaDataImport::FindMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="93dc0-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="93dc0-103">Pobiera wskaźnik do MethodDef tokenu dla metody, która jest ujęta w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.</span><span class="sxs-lookup"><span data-stu-id="93dc0-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93dc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93dc0-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93dc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93dc0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="93dc0-106">[in] `mdTypeDef` Tokenu dla typu (klasę lub interfejs), który otacza elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="93dc0-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="93dc0-107">Jeśli ta wartość jest `mdTokenNil`, a następnie wyszukiwanie jest wykonywane na potrzeby funkcją globalną.</span><span class="sxs-lookup"><span data-stu-id="93dc0-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="93dc0-108">[in] Nazwa metody do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="93dc0-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="93dc0-109">[in] Wskaźnik do binarnych metadanych podpis metody.</span><span class="sxs-lookup"><span data-stu-id="93dc0-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="93dc0-110">[in] Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="93dc0-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="93dc0-111">[out] Wskaźnik do zgodnego tokenu MethodDef.</span><span class="sxs-lookup"><span data-stu-id="93dc0-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93dc0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93dc0-112">Remarks</span></span>  
 <span data-ttu-id="93dc0-113">Określ metody przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="93dc0-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="93dc0-114">Może istnieć wiele metod o tej samej nazwie w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="93dc0-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="93dc0-115">W takim przypadku należy przekazać sygnaturę metody i nie może znaleźć unikatowego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="93dc0-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="93dc0-116">Podpis jest przekazywany do `FindMethod` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="93dc0-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="93dc0-117">Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="93dc0-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="93dc0-118">Token jest to indeks w lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="93dc0-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="93dc0-119">Nie można tworzyć sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i za ten podpis jako dane wejściowe do wprowadzania `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="93dc0-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 `FindMethod` <span data-ttu-id="93dc0-120">Umożliwia znalezienie tylko tych metod, które zostały zdefiniowane bezpośrednio klasę lub interfejs; nie odnajdzie metody dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="93dc0-120">finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93dc0-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93dc0-121">Requirements</span></span>  
 <span data-ttu-id="93dc0-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93dc0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93dc0-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="93dc0-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93dc0-124">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93dc0-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="93dc0-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="93dc0-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="93dc0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93dc0-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="93dc0-127">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93dc0-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="93dc0-128">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93dc0-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
