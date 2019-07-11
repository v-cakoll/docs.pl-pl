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
ms.openlocfilehash: 1baee71b5b8575f51eb54fbc8a037a5dddd24500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782523"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="33901-102">IMetaDataImport::FindField — Metoda</span><span class="sxs-lookup"><span data-stu-id="33901-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="33901-103">Pobiera wskaźnik do FieldDef tokenu dla pola, który jest ujęty w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.</span><span class="sxs-lookup"><span data-stu-id="33901-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33901-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33901-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33901-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33901-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="33901-106">[in] Token element TypeDef dla klasy lub interfejsu, który otacza pole wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="33901-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="33901-107">Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane dla zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="33901-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="33901-108">[in] Nazwa pola do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="33901-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="33901-109">[in] Wskaźnik do podpisu metadanych binarne pola.</span><span class="sxs-lookup"><span data-stu-id="33901-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="33901-110">[in] Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="33901-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="33901-111">[out] Wskaźnik do zgodnego tokenu FieldDef.</span><span class="sxs-lookup"><span data-stu-id="33901-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33901-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33901-112">Remarks</span></span>  
 <span data-ttu-id="33901-113">Określ pola przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="33901-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="33901-114">Podpis jest przekazywany do `FindField` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="33901-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="33901-115">Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości.</span><span class="sxs-lookup"><span data-stu-id="33901-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="33901-116">(Token jest to indeks w lokalnej tabeli TypeDef).</span><span class="sxs-lookup"><span data-stu-id="33901-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="33901-117">Nie można tworzenia sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i używać tego podpisu jako dane wejściowe `FindField`.</span><span class="sxs-lookup"><span data-stu-id="33901-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="33901-118">`FindField` Umożliwia znalezienie tylko pola, które zostały zdefiniowane bezpośrednio klasę lub interfejs; nie odnajdzie odziedziczonego pola.</span><span class="sxs-lookup"><span data-stu-id="33901-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33901-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33901-119">Requirements</span></span>  
 <span data-ttu-id="33901-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33901-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33901-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="33901-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33901-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33901-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33901-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33901-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33901-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33901-124">See also</span></span>

- [<span data-ttu-id="33901-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="33901-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="33901-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="33901-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
