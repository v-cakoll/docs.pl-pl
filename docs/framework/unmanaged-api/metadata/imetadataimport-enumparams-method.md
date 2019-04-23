---
title: IMetaDataImport::EnumParams — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed5ddd74e61e63426871f659aa1c962d38fd534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221404"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="4eaab-102">IMetaDataImport::EnumParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="4eaab-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="4eaab-103">Wylicza tokenów ParamDef reprezentującą parametry metody odwołuje się określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="4eaab-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eaab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4eaab-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eaab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4eaab-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4eaab-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="4eaab-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4eaab-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="4eaab-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="4eaab-108">[in] Token MethodDef reprezentujący metodę z parametrami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4eaab-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="4eaab-109">[out] Tablica do przechowywania tokenów ParamDef.</span><span class="sxs-lookup"><span data-stu-id="4eaab-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4eaab-110">[in] Maksymalny rozmiar `rParams` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4eaab-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4eaab-111">[out] Liczba tokenów ParamDef zwracane w `rParams`.</span><span class="sxs-lookup"><span data-stu-id="4eaab-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4eaab-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4eaab-112">Return Value</span></span>  
  
|<span data-ttu-id="4eaab-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4eaab-113">HRESULT</span></span>|<span data-ttu-id="4eaab-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4eaab-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4eaab-115">`EnumParams` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4eaab-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4eaab-116">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4eaab-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="4eaab-117">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="4eaab-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4eaab-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4eaab-118">Requirements</span></span>  
 <span data-ttu-id="4eaab-119">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eaab-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eaab-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4eaab-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4eaab-121">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4eaab-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4eaab-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eaab-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eaab-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4eaab-123">See also</span></span>

- [<span data-ttu-id="4eaab-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="4eaab-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4eaab-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4eaab-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
