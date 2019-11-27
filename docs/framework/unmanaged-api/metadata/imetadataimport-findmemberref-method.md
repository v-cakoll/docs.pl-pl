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
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437958"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="6ec1c-102">IMetaDataImport::FindMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ec1c-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="6ec1c-103">Pobiera wskaźnik do tokenu MemberRef dla odwołania do elementu członkowskiego, który jest ujęty w określony <xref:System.Type> i ma określoną nazwę i sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ec1c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ec1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ec1c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6ec1c-106">podczas Token TypeRef dla klasy lub interfejsu, który obejmuje odwołanie do elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="6ec1c-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane dla zmiennej globalnej lub odwołania do funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="6ec1c-108">podczas Nazwa odwołania do elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6ec1c-109">podczas Wskaźnik do binarnego podpisu metadanych odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6ec1c-110">podczas Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="6ec1c-111">określoną Wskaźnik do zgodnego tokenu elementu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ec1c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ec1c-112">Remarks</span></span>  
 <span data-ttu-id="6ec1c-113">Należy określić składową przy użyciu jej klasy lub interfejsu (`td`), jej nazwy (`szName`) i opcjonalnie jej sygnatury (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="6ec1c-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="6ec1c-114">Sygnatura przeniesiona do `FindMemberRef` musi być wygenerowana w bieżącym zakresie, ponieważ sygnatury są powiązane z konkretnym zakresem.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="6ec1c-115">Podpis może osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="6ec1c-116">Token jest indeksem tabeli lokalnych TypeDef.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="6ec1c-117">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu i użyć tej sygnatury jako danych wejściowych do `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="6ec1c-118">`FindMemberRef` odnajduje tylko odwołania elementu członkowskiego, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znaleziono dziedziczonych odwołań do członków.</span><span class="sxs-lookup"><span data-stu-id="6ec1c-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec1c-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ec1c-119">Requirements</span></span>  
 <span data-ttu-id="6ec1c-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec1c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec1c-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6ec1c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ec1c-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ec1c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ec1c-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec1c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec1c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ec1c-124">See also</span></span>

- [<span data-ttu-id="6ec1c-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ec1c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6ec1c-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ec1c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
