---
title: IMetaDataImport::GetEventProps — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177269"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="a1f10-102">IMetaDataImport::GetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1f10-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="a1f10-103">Pobiera informacje o metadanych dla zdarzenia reprezentowane przez token określonego zdarzenia, w tym typ deklarowania, dodawanie i usuwanie metod delegatów i wszelkie flagi i inne skojarzone dane.</span><span class="sxs-lookup"><span data-stu-id="a1f10-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1f10-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a1f10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1f10-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="a1f10-106">[w] Token metadanych zdarzenia reprezentujący zdarzenie, dla które można uzyskać metadane.</span><span class="sxs-lookup"><span data-stu-id="a1f10-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="a1f10-107">[na zewnątrz] Wskaźnik do TypeDef token reprezentujący klasę, która deklaruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a1f10-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="a1f10-108">[na zewnątrz] Nazwa zdarzenia, do którego `ev`odwołuje się .</span><span class="sxs-lookup"><span data-stu-id="a1f10-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="a1f10-109">[w] Żądana długość w szerokich znakach `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="a1f10-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="a1f10-110">[na zewnątrz] Zwrócona długość w `szEvent`szerokich znakach .</span><span class="sxs-lookup"><span data-stu-id="a1f10-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="a1f10-111">[na zewnątrz] Wskaźnik do typeref lub TypeDef token metadanych reprezentujących <xref:System.Delegate> typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a1f10-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="a1f10-112">[na zewnątrz] Wskaźnik do tokenu metadanych reprezentujący metodę, która dodaje programy obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a1f10-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="a1f10-113">[na zewnątrz] Wskaźnik do tokenu metadanych reprezentujący metodę, która usuwa programy obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a1f10-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="a1f10-114">[na zewnątrz] Wskaźnik do tokenu metadanych reprezentujący metodę, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a1f10-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="a1f10-115">[na zewnątrz] Tablica wskaźników tokenu do innych metod skojarzonych ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="a1f10-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a1f10-116">[w] Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a1f10-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="a1f10-117">[na zewnątrz] Liczba tokenów zwróconych `rmdOtherMethod`w .</span><span class="sxs-lookup"><span data-stu-id="a1f10-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f10-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1f10-118">Requirements</span></span>  
 <span data-ttu-id="a1f10-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f10-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f10-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="a1f10-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1f10-121">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1f10-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1f10-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f10-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f10-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1f10-123">See also</span></span>

- [<span data-ttu-id="a1f10-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1f10-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a1f10-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1f10-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
