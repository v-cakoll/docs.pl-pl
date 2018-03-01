---
title: "IMetaDataImport::GetEventProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73f257c46fd21355eeaabbe9e1b5d2841d2c3911
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="3ea47-102">IMetaDataImport::GetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ea47-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="3ea47-103">Pobiera metadane dla zdarzenia reprezentowany przez token określonego zdarzenia, w tym typ deklarujący, Dodaj i Usuń metody delegatów i flagi oraz inne powiązane dane.</span><span class="sxs-lookup"><span data-stu-id="3ea47-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ea47-104">Syntax</span></span>  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ea47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ea47-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="3ea47-106">[in] Token metadanych zdarzeń reprezentujący zdarzeń można pobrać metadanych.</span><span class="sxs-lookup"><span data-stu-id="3ea47-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="3ea47-107">[out] Wskaźnik do TypeDef token reprezentujący klasę, która deklaruje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3ea47-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="3ea47-108">[out] Nazwa zdarzenia odwołuje się `ev`.</span><span class="sxs-lookup"><span data-stu-id="3ea47-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="3ea47-109">[in] Żądana długość w znakach szerokości `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="3ea47-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="3ea47-110">[out] Długość zwróconych w znaki dwubajtowe `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="3ea47-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="3ea47-111">[out] Wskaźnik do elementu TypeRef lub TypeDef metadanych token reprezentujący <xref:System.Delegate> typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3ea47-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="3ea47-112">[out] Wskaźnik do tokenu metadanych reprezentujący metodę, która dodaje obsługę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3ea47-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="3ea47-113">[out] Wskaźnik do tokenu metadanych reprezentujący metodę, która usuwa programy obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3ea47-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="3ea47-114">[out] Wskaźnik do tokenu metadanych reprezentujący metodę, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="3ea47-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="3ea47-115">[out] Tablica tokenu wskaźników do innych metod, skojarzone ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="3ea47-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3ea47-116">[in] Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="3ea47-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="3ea47-117">[out] Liczba tokenów zwracanych w `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="3ea47-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea47-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ea47-118">Requirements</span></span>  
 <span data-ttu-id="3ea47-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea47-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea47-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ea47-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ea47-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ea47-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ea47-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea47-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea47-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ea47-123">See Also</span></span>  
 [<span data-ttu-id="3ea47-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ea47-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3ea47-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ea47-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
