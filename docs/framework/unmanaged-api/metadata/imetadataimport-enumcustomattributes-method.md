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
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175528"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="1865f-102">IMetaDataImport::EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="1865f-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="1865f-103">Wylicza tokeny niestandardowej definicji atrybutów skojarzone z określonym typem lub elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="1865f-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1865f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1865f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1865f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1865f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1865f-106">[w, na zewnątrz] Wskaźnik do zwróconego wylicznika.</span><span class="sxs-lookup"><span data-stu-id="1865f-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="1865f-107">[w] Token dla zakresu wyliczenia lub zero dla wszystkich atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1865f-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="1865f-108">[w] Token dla konstruktora typu atrybutów, które mają być `null` wyliczone lub dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="1865f-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="1865f-109">[na zewnątrz] Tablica niestandardowych tokenów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1865f-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1865f-110">[w] Maksymalny rozmiar `rCustomAttributes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1865f-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="1865f-111">[out, opcjonalnie] Rzeczywista liczba wartości tokenów zwrócona w `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="1865f-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1865f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1865f-112">Return Value</span></span>  
  
|<span data-ttu-id="1865f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1865f-113">HRESULT</span></span>|<span data-ttu-id="1865f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1865f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1865f-115">`EnumCustomAttributes`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1865f-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1865f-116">Nie ma żadnych atrybutów niestandardowych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1865f-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="1865f-117">W takim `pcCustomAttributes` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="1865f-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1865f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1865f-118">Requirements</span></span>  
 <span data-ttu-id="1865f-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1865f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1865f-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="1865f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1865f-121">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1865f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1865f-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1865f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1865f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1865f-123">See also</span></span>

- [<span data-ttu-id="1865f-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1865f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1865f-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1865f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
