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
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503669"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="dd0aa-102">IMetaDataImport::FindField — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd0aa-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="dd0aa-103">Pobiera wskaźnik do tokenu FieldDef dla pola, które jest ujęte w określonym <xref:System.Type> i który ma określoną nazwę i sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd0aa-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd0aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd0aa-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dd0aa-106">podczas Token TypeDef dla klasy lub interfejsu, który obejmuje pole, które ma zostać wyszukane.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="dd0aa-107">Jeśli ta wartość jest `mdTokenNil` , wyszukiwanie jest wykonywane dla zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="dd0aa-108">podczas Nazwa pola, które ma zostać wyszukane.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="dd0aa-109">podczas Wskaźnik do binarnego podpisu metadanych pola.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="dd0aa-110">podczas Rozmiar w bajtach `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="dd0aa-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="dd0aa-111">określoną Wskaźnik do zgodnego tokenu FieldDef.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd0aa-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd0aa-112">Remarks</span></span>  
 <span data-ttu-id="dd0aa-113">Należy określić pole przy użyciu jego klasy lub interfejsu ( `td` ), jego nazwy ( `szName` ) i opcjonalnie jego sygnatury ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="dd0aa-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="dd0aa-114">Sygnatura przekazano do `FindField` musi być wygenerowana w bieżącym zakresie, ponieważ sygnatury są powiązane z konkretnym zakresem.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="dd0aa-115">Podpis może osadzić token, który identyfikuje otaczającą klasę lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="dd0aa-116">(Token jest indeksem w lokalnej tabeli TypeDef).</span><span class="sxs-lookup"><span data-stu-id="dd0aa-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="dd0aa-117">Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego zakresu i użyć tej sygnatury jako danych wejściowych `FindField` .</span><span class="sxs-lookup"><span data-stu-id="dd0aa-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="dd0aa-118">`FindField`znajduje tylko pola, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajdują się w nim dziedziczone pola.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd0aa-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd0aa-119">Requirements</span></span>  
 <span data-ttu-id="dd0aa-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0aa-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0aa-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dd0aa-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd0aa-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd0aa-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd0aa-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0aa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0aa-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd0aa-124">See also</span></span>

- [<span data-ttu-id="dd0aa-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd0aa-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="dd0aa-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd0aa-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
