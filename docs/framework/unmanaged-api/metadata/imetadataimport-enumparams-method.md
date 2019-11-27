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
ms.openlocfilehash: e5fa3647c86d97730e7ad6a2576dd34af75251d6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433958"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="92e51-102">IMetaDataImport::EnumParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="92e51-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="92e51-103">Wylicza tokeny ParamDef reprezentujące parametry metody przywoływanej przez określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="92e51-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92e51-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92e51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92e51-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="92e51-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="92e51-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="92e51-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="92e51-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="92e51-108">podczas Token MethodDef reprezentujący metodę z parametrami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="92e51-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="92e51-109">określoną Tablica służąca do przechowywania tokenów ParamDef.</span><span class="sxs-lookup"><span data-stu-id="92e51-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="92e51-110">podczas Maksymalny rozmiar tablicy `rParams`.</span><span class="sxs-lookup"><span data-stu-id="92e51-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="92e51-111">określoną Liczba tokenów ParamDef zwróconych w `rParams`.</span><span class="sxs-lookup"><span data-stu-id="92e51-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92e51-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92e51-112">Return Value</span></span>  
  
|<span data-ttu-id="92e51-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92e51-113">HRESULT</span></span>|<span data-ttu-id="92e51-114">Opis</span><span class="sxs-lookup"><span data-stu-id="92e51-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="92e51-115">`EnumParams` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="92e51-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="92e51-116">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="92e51-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="92e51-117">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="92e51-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92e51-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92e51-118">Requirements</span></span>  
 <span data-ttu-id="92e51-119">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92e51-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e51-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="92e51-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92e51-121">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92e51-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92e51-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e51-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e51-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92e51-123">See also</span></span>

- [<span data-ttu-id="92e51-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="92e51-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="92e51-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="92e51-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
