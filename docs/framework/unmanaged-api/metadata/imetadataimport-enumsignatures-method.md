---
title: "IMetaDataImport::EnumSignatures — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumSignatures
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d47e2512103947f007c81450157a0b3e334a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="a6788-102">IMetaDataImport::EnumSignatures — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6788-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="a6788-103">Wylicza tokeny sygnatury reprezentujący autonomicznej podpisów w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="a6788-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6788-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6788-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6788-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6788-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a6788-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a6788-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a6788-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="a6788-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="a6788-108">[out] Tablica używany do przechowywania tokenów podpisu.</span><span class="sxs-lookup"><span data-stu-id="a6788-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a6788-109">[in] Maksymalny rozmiar `rSignatures` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a6788-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="a6788-110">[out] Liczba tokenów podpisu zwracane w `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="a6788-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6788-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a6788-111">Return Value</span></span>  
  
|<span data-ttu-id="a6788-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6788-112">HRESULT</span></span>|<span data-ttu-id="a6788-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a6788-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a6788-114">`EnumSignatures`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a6788-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a6788-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a6788-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a6788-116">W takim przypadku `pcSignatures` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="a6788-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6788-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6788-117">Remarks</span></span>  
 <span data-ttu-id="a6788-118">Podpis tokenów są tworzone przez [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a6788-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6788-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6788-119">Requirements</span></span>  
 <span data-ttu-id="a6788-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6788-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6788-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6788-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6788-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6788-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6788-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6788-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6788-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6788-124">See Also</span></span>  
 [<span data-ttu-id="a6788-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6788-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a6788-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6788-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
