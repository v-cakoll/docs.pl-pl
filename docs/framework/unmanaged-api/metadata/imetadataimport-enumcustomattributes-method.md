---
title: IMetaDataImport::EnumCustomAttributes — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b80bb7b62d3a4ffee61cc6756b7d7d02f2b074bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196206"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="bb77b-102">IMetaDataImport::EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb77b-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="bb77b-103">Wylicza tokeny niestandardowe definicja atrybutu skojarzone z określonego typu lub składowej.</span><span class="sxs-lookup"><span data-stu-id="bb77b-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb77b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb77b-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb77b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb77b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bb77b-106">[out w] Wskaźnik do zwróconego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="bb77b-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="bb77b-107">[in] Token do zakresu wyliczenia lub wartość zero dla wszystkich atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb77b-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="bb77b-108">[in] Token dla konstruktora typu atrybutów, które mają zostać wyliczone, lub `null` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="bb77b-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="bb77b-109">[out] Tablica atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb77b-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bb77b-110">[in] Maksymalny rozmiar `rCustomAttributes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="bb77b-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="bb77b-111">[out, opcjonalny] Rzeczywista liczba tokenów wartości zwracanych w `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="bb77b-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb77b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb77b-112">Return Value</span></span>  
  
|<span data-ttu-id="bb77b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb77b-113">HRESULT</span></span>|<span data-ttu-id="bb77b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bb77b-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` <span data-ttu-id="bb77b-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="bb77b-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bb77b-116">Nie istnieją żadne atrybuty niestandardowe do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bb77b-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="bb77b-117">W takim przypadku `pcCustomAttributes` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="bb77b-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb77b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb77b-118">Requirements</span></span>  
 <span data-ttu-id="bb77b-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb77b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb77b-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bb77b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb77b-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb77b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bb77b-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bb77b-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb77b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb77b-123">See also</span></span>

- [<span data-ttu-id="bb77b-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bb77b-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bb77b-125">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bb77b-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
