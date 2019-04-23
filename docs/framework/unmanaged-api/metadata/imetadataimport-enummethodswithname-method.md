---
title: IMetaDataImport::EnumMethodsWithName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200184"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="00686-102">IMetaDataImport::EnumMethodsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="00686-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="00686-103">Wylicza metod, które mają określoną nazwą i które są definiowane przez typ odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="00686-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00686-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00686-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00686-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00686-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="00686-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="00686-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="00686-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="00686-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="00686-108">[in] TypeDef token reprezentujący typ, którego metody wyliczania.</span><span class="sxs-lookup"><span data-stu-id="00686-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="00686-109">[in] Nazwa która ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="00686-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="00686-110">[out] Tablica do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="00686-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="00686-111">[in] Maksymalny rozmiar `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="00686-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="00686-112">[out] Liczba tokenów MethodDef zwracane w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="00686-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00686-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00686-113">Remarks</span></span>  
 <span data-ttu-id="00686-114">Ta metoda wylicza pola i metody, ale nie do właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="00686-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="00686-115">W odróżnieniu od [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` odrzuca wszystkie tokeny metody, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="00686-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00686-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="00686-116">Return Value</span></span>  
  
|<span data-ttu-id="00686-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00686-117">HRESULT</span></span>|<span data-ttu-id="00686-118">Opis</span><span class="sxs-lookup"><span data-stu-id="00686-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="00686-119">`EnumMethodsWithName` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="00686-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="00686-120">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="00686-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="00686-121">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="00686-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00686-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00686-122">Requirements</span></span>  
 <span data-ttu-id="00686-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00686-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00686-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="00686-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00686-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00686-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00686-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00686-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00686-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00686-127">See also</span></span>

- [<span data-ttu-id="00686-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="00686-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="00686-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="00686-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
