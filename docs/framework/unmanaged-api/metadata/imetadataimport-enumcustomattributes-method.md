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
ms.openlocfilehash: c38b7f060c34f7408195484dec2c49305db422fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781321"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="d9920-102">IMetaDataImport::EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9920-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="d9920-103">Wylicza tokeny niestandardowe definicja atrybutu skojarzone z określonego typu lub składowej.</span><span class="sxs-lookup"><span data-stu-id="d9920-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9920-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9920-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d9920-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9920-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d9920-106">[out w] Wskaźnik do zwróconego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="d9920-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="d9920-107">[in] Token do zakresu wyliczenia lub wartość zero dla wszystkich atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d9920-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d9920-108">[in] Token dla konstruktora typu atrybutów, które mają zostać wyliczone, lub `null` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="d9920-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="d9920-109">[out] Tablica atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d9920-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d9920-110">[in] Maksymalny rozmiar `rCustomAttributes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d9920-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="d9920-111">[out, opcjonalny] Rzeczywista liczba tokenów wartości zwracanych w `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="d9920-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9920-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d9920-112">Return Value</span></span>  
  
|<span data-ttu-id="d9920-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9920-113">HRESULT</span></span>|<span data-ttu-id="d9920-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d9920-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d9920-115">`EnumCustomAttributes` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d9920-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d9920-116">Nie istnieją żadne atrybuty niestandardowe do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d9920-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="d9920-117">W takim przypadku `pcCustomAttributes` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="d9920-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9920-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9920-118">Requirements</span></span>  
 <span data-ttu-id="d9920-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9920-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9920-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d9920-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9920-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9920-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9920-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9920-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9920-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9920-123">See also</span></span>

- [<span data-ttu-id="d9920-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9920-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d9920-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9920-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
