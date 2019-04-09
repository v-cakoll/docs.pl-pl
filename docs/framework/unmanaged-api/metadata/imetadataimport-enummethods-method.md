---
title: IMetaDataImport::EnumMethods — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bab625b8415183b9cf90c35cba140c4d28095805
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076877"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="5790d-102">IMetaDataImport::EnumMethods — Metoda</span><span class="sxs-lookup"><span data-stu-id="5790d-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="5790d-103">Wylicza tokenów MethodDef reprezentujący metody określonego typu.</span><span class="sxs-lookup"><span data-stu-id="5790d-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5790d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5790d-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5790d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5790d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5790d-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="5790d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5790d-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="5790d-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="5790d-108">[in] TypeDef token reprezentujący typ z metody służące do wyliczania.</span><span class="sxs-lookup"><span data-stu-id="5790d-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="5790d-109">[out] Tablica do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="5790d-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5790d-110">[in] Maksymalny rozmiar MethodDef `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="5790d-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5790d-111">[out] Liczba tokenów MethodDef zwracane w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="5790d-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5790d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5790d-112">Return Value</span></span>  
  
|<span data-ttu-id="5790d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5790d-113">HRESULT</span></span>|<span data-ttu-id="5790d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5790d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethods` <span data-ttu-id="5790d-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5790d-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5790d-116">Nie ma żadnych tokeny MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5790d-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="5790d-117">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="5790d-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5790d-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5790d-118">Requirements</span></span>  
 <span data-ttu-id="5790d-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5790d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5790d-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5790d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5790d-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5790d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5790d-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5790d-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5790d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5790d-123">See also</span></span>

- [<span data-ttu-id="5790d-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5790d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5790d-125">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5790d-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
