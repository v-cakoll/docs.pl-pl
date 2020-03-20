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
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175424"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="cb807-102">IMetaDataImport::FindMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb807-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="cb807-103">Pobiera wskaźnik do tokenu MemberRef dla odwołania elementu członkowskiego, który jest ujęty przez określony <xref:System.Type> i który ma określoną nazwę i podpis metadanych.</span><span class="sxs-lookup"><span data-stu-id="cb807-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb807-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb807-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb807-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb807-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cb807-106">[w] TypeRef token dla klasy lub interfejsu, który otacza odwołanie do elementu członkowskiego do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cb807-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="cb807-107">Jeśli ta `mdTokenNil`wartość jest , wyszukiwanie jest wykonywane dla zmiennej globalnej lub odwołania funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="cb807-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="cb807-108">[w] Nazwa odwołania elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="cb807-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="cb807-109">[w] Wskaźnik do podpisu binarnych metadanych odwołania elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cb807-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="cb807-110">[w] Rozmiar w bajtach . `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="cb807-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="cb807-111">[na zewnątrz] Wskaźnik do pasującego tokenu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="cb807-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb807-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb807-112">Remarks</span></span>  
 <span data-ttu-id="cb807-113">Element członkowski można określić za`td`pomocą otaczającej`szName`go klasy lub`pvSigBlob`interfejsu ( ), jego nazwy ( i opcjonalnie jego podpisu ( ).</span><span class="sxs-lookup"><span data-stu-id="cb807-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="cb807-114">Podpis przekazany `FindMemberRef` do musi zostały wygenerowane w bieżącym zakresie, ponieważ podpisy są powiązane z określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="cb807-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="cb807-115">Podpis można osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="cb807-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="cb807-116">Token jest indeksem do lokalnej tabeli TypeDef.</span><span class="sxs-lookup"><span data-stu-id="cb807-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="cb807-117">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego `FindMemberRef`zakresu i użyć tego podpisu jako danych wejściowych do .</span><span class="sxs-lookup"><span data-stu-id="cb807-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="cb807-118">`FindMemberRef`znajduje tylko odwołania do elementów członkowskich, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje dziedziczonych odwołań do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="cb807-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb807-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb807-119">Requirements</span></span>  
 <span data-ttu-id="cb807-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb807-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb807-121">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb807-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb807-122">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb807-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb807-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb807-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb807-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb807-124">See also</span></span>

- [<span data-ttu-id="cb807-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cb807-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cb807-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb807-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
