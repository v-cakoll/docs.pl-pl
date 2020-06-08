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
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491306"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="e5c5e-102">IMetaDataImport::GetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5c5e-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="e5c5e-103">Pobiera informacje o metadanych dla zdarzenia reprezentowanego przez określony token zdarzenia, w tym typ deklarujący, metody dodawania i usuwania dla delegatów oraz wszelkie flagi i inne skojarzone dane.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5c5e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e5c5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5c5e-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="e5c5e-106">podczas Token metadanych zdarzenia, który reprezentuje zdarzenie, dla którego mają zostać pobrane metadane.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="e5c5e-107">określoną Wskaźnik do tokenu TypeDef reprezentujący klasę, która deklaruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="e5c5e-108">określoną Nazwa zdarzenia, do którego odwołuje się `ev` .</span><span class="sxs-lookup"><span data-stu-id="e5c5e-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="e5c5e-109">podczas Żądana długość w postaci znaków dwubajtowych `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="e5c5e-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="e5c5e-110">określoną Długość zwrócona w znaki dwubajtowe z `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="e5c5e-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="e5c5e-111">określoną Wskaźnik do tokenu metadanych elementu TypeRef lub TypeDef reprezentujący <xref:System.Delegate> Typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="e5c5e-112">określoną Wskaźnik do tokenu metadanych reprezentującej metodę, która dodaje procedury obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="e5c5e-113">określoną Wskaźnik do tokenu metadanych reprezentująca metodę, która usuwa procedury obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="e5c5e-114">określoną Wskaźnik do tokenu metadanych reprezentująca metodę, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="e5c5e-115">określoną Tablica wskaźników tokenów z innymi metodami skojarzonymi ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e5c5e-116">podczas Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e5c5e-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="e5c5e-117">określoną Liczba tokenów zwróconych w `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="e5c5e-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c5e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5c5e-118">Requirements</span></span>  
 <span data-ttu-id="e5c5e-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c5e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c5e-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e5c5e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5c5e-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e5c5e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5c5e-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c5e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c5e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5c5e-123">See also</span></span>

- [<span data-ttu-id="e5c5e-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5c5e-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e5c5e-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5c5e-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
