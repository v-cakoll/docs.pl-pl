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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c87f2212c761dc31a75addabca6970c5497aa2a0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782430"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="ca008-102">IMetaDataImport::GetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca008-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="ca008-103">Pobiera informacje o metadanych dla zdarzenia, reprezentowane przez token określonego zdarzenia, w tym typ deklarujący, Dodaj i Usuń metody obiektów delegowanych, flag i inne powiązane dane.</span><span class="sxs-lookup"><span data-stu-id="ca008-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca008-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca008-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ca008-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca008-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="ca008-106">[in] Token metadanych zdarzenia reprezentujący zdarzeń, które można pobrać metadanych.</span><span class="sxs-lookup"><span data-stu-id="ca008-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ca008-107">[out] Wskaźnik do TypeDef token reprezentujący klasę, która deklaruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ca008-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="ca008-108">[out] Nazwa zdarzenia odwołuje się `ev`.</span><span class="sxs-lookup"><span data-stu-id="ca008-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="ca008-109">[in] Żądana długość w znaków `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="ca008-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="ca008-110">[out] Zwrócona długość w znakach szerokiego `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="ca008-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="ca008-111">[out] Wskaźnik do TypeRef lub TypeDef metadanych token reprezentujący <xref:System.Delegate> typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ca008-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="ca008-112">[out] Wskaźnik do tokenu metadanych reprezentujący metodę, która dodaje programy obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ca008-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="ca008-113">[out] Wskaźnik do tokenu metadanych reprezentujący metodę, która usuwa programy obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ca008-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="ca008-114">[out] Wskaźnik do tokenu metadanych reprezentujący metodę, która wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ca008-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="ca008-115">[out] Tablica wskaźników tokenu do innych metod, skojarzone ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="ca008-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ca008-116">[in] Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ca008-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="ca008-117">[out] Liczba zwracane w tokenach `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="ca008-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca008-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca008-118">Requirements</span></span>  
 <span data-ttu-id="ca008-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca008-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca008-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ca008-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca008-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca008-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca008-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca008-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca008-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca008-123">See also</span></span>

- [<span data-ttu-id="ca008-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca008-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ca008-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca008-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
