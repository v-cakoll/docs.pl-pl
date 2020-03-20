---
title: IMetaDataImport2::EnumMethodSpecs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177171"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="d567b-102">IMetaDataImport2::EnumMethodSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="d567b-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="d567b-103">Pobiera wyliczenia dla tablicy Tokeny MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.</span><span class="sxs-lookup"><span data-stu-id="d567b-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d567b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d567b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d567b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d567b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d567b-106">[w, na zewnątrz] Wskaźnik do wyliczacza `rMethodSpecs`dla .</span><span class="sxs-lookup"><span data-stu-id="d567b-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="d567b-107">[w] The MemberRef lub MethodDef token, który reprezentuje metodę, której tokeny MethodSpec mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="d567b-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="d567b-108">Jeśli wartość `tk` wynosi 0 (zero), wszystkie tokeny MethodSpec w zakresie zostaną wyliczone.</span><span class="sxs-lookup"><span data-stu-id="d567b-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="d567b-109">[na zewnątrz] Tablica tokenów MethodSpec do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d567b-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d567b-110">[w] Żądana maksymalna liczba tokenów `rMethodSpecs`do umieszczenia w .</span><span class="sxs-lookup"><span data-stu-id="d567b-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="d567b-111">[na zewnątrz] Zwrócona liczba tokenów `rMethodSpecs`umieszczonych w .</span><span class="sxs-lookup"><span data-stu-id="d567b-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d567b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d567b-112">Return Value</span></span>  
  
|<span data-ttu-id="d567b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d567b-113">HRESULT</span></span>|<span data-ttu-id="d567b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d567b-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d567b-115">`EnumMethodSpecs`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d567b-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d567b-116">`phEnum`nie ma elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d567b-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="d567b-117">W takim `pcMethodSpecs` przypadku jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="d567b-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d567b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d567b-118">Requirements</span></span>  
 <span data-ttu-id="d567b-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d567b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d567b-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="d567b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d567b-121">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d567b-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d567b-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d567b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d567b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d567b-123">See also</span></span>

- [<span data-ttu-id="d567b-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d567b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="d567b-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d567b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
