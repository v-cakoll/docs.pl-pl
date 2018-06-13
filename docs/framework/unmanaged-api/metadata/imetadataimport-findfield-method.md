---
title: IMetaDataImport::FindField — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac69bab45ccd39b6a055fe4d2f74950ab47da779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447035"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="a09f1-102">IMetaDataImport::FindField — Metoda</span><span class="sxs-lookup"><span data-stu-id="a09f1-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="a09f1-103">Pobiera wskaźnik do FieldDef token pola, które jest ujęte przez określony <xref:System.Type> z określoną sygnaturą nazwy i metadanych.</span><span class="sxs-lookup"><span data-stu-id="a09f1-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a09f1-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a09f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a09f1-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a09f1-106">[in] Token TypeDef dla klasy lub interfejsu, który umieszcza pole wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a09f1-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="a09f1-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="a09f1-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="a09f1-108">[in] Nazwa pola do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="a09f1-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a09f1-109">[in] Wskaźnik do metadanych binarne podpis pola.</span><span class="sxs-lookup"><span data-stu-id="a09f1-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a09f1-110">[in] Wyrażony w bajtach rozmiar `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a09f1-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="a09f1-111">[out] Wskaźnik do dopasowania tokenie FieldDef.</span><span class="sxs-lookup"><span data-stu-id="a09f1-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a09f1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a09f1-112">Remarks</span></span>  
 <span data-ttu-id="a09f1-113">Określ pola przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="a09f1-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="a09f1-114">Podpis przekazany do `FindField` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="a09f1-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="a09f1-115">Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="a09f1-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="a09f1-116">(Token jest indeks do lokalnej tabeli TypeDef).</span><span class="sxs-lookup"><span data-stu-id="a09f1-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="a09f1-117">Nie kompilacji podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używają tego podpisu jako dane wejściowe `FindField`.</span><span class="sxs-lookup"><span data-stu-id="a09f1-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="a09f1-118">`FindField` Wyszukuje tylko pola, które zostały zdefiniowane bezpośrednio w klasy lub interfejsu; pola dziedziczonych nie zostanie znaleziona.</span><span class="sxs-lookup"><span data-stu-id="a09f1-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09f1-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a09f1-119">Requirements</span></span>  
 <span data-ttu-id="a09f1-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a09f1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09f1-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a09f1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a09f1-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a09f1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a09f1-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09f1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09f1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a09f1-124">See Also</span></span>  
 [<span data-ttu-id="a09f1-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a09f1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a09f1-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a09f1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
