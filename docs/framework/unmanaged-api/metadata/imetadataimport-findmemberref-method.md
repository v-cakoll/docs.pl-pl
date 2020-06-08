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
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491667"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="7ab26-102">IMetaDataImport::FindMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ab26-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="7ab26-103">Pobiera wskaźnik do tokenu MemberRef dla odwołania do elementu członkowskiego, który jest ujęty w określony <xref:System.Type> i który ma określoną nazwę i sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="7ab26-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab26-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ab26-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ab26-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7ab26-106">podczas Token TypeRef dla klasy lub interfejsu, który obejmuje odwołanie do elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="7ab26-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="7ab26-107">Jeśli ta wartość jest `mdTokenNil` , wyszukiwanie jest wykonywane dla zmiennej globalnej lub odwołania do funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="7ab26-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="7ab26-108">podczas Nazwa odwołania do elementu członkowskiego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="7ab26-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7ab26-109">podczas Wskaźnik do binarnego podpisu metadanych odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7ab26-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7ab26-110">podczas Rozmiar w bajtach `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="7ab26-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="7ab26-111">określoną Wskaźnik do zgodnego tokenu elementu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="7ab26-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab26-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ab26-112">Remarks</span></span>  
 <span data-ttu-id="7ab26-113">Należy określić składową przy użyciu jej klasy lub interfejsu ( `td` ), jej nazwy ( `szName` ) i opcjonalnie jej sygnatury ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="7ab26-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="7ab26-114">Sygnatura przekazano do `FindMemberRef` musi być wygenerowana w bieżącym zakresie, ponieważ sygnatury są powiązane z konkretnym zakresem.</span><span class="sxs-lookup"><span data-stu-id="7ab26-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="7ab26-115">Podpis może osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="7ab26-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="7ab26-116">Token jest indeksem tabeli lokalnych TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7ab26-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="7ab26-117">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu i użyć tej sygnatury jako danych wejściowych `FindMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="7ab26-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="7ab26-118">`FindMemberRef`znajduje tylko odwołania do elementu członkowskiego, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znaleziono dziedziczonych odwołań do członków.</span><span class="sxs-lookup"><span data-stu-id="7ab26-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab26-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ab26-119">Requirements</span></span>  
 <span data-ttu-id="7ab26-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab26-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab26-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7ab26-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ab26-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7ab26-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ab26-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab26-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab26-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ab26-124">See also</span></span>

- [<span data-ttu-id="7ab26-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7ab26-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7ab26-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ab26-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
