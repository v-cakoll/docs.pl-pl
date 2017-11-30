---
title: "IMetaDataEmit::GetSaveSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9686e8e2c4e8276e725852cb58fac7ed1973778b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="ff420-102">IMetaDataEmit::GetSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff420-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="ff420-103">Pobiera szacowany rozmiar binarne zestaw i jego metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ff420-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff420-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff420-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff420-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff420-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="ff420-106">[in] Wartość [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wyliczenia, która określa, czy można uzyskać dokładne i przybliżony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="ff420-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="ff420-107">Tylko trzy wartości są prawidłowe: cssAccurate, cssQuick i cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="ff420-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="ff420-108">cssAccurate Zwraca dokładną Zapisz rozmiar, ale trwa dłużej do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ff420-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="ff420-109">cssQuick zwraca rozmiar, uzupełniona na potrzeby bezpieczeństwa, ale zajmuje mniej czasu do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ff420-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="ff420-110">Określa, że cssDiscardTransientCAs `GetSaveSize` czy go można wyrzucać discardable atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ff420-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="ff420-111">[out] Wskaźnik do rozmiaru, który jest wymagany do zapisania pliku.</span><span class="sxs-lookup"><span data-stu-id="ff420-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff420-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff420-112">Remarks</span></span>  
 <span data-ttu-id="ff420-113">`GetSaveSize`oblicza przestrzeni wymaganej w bajtach, aby zapisać zestawu i wszystkich jego metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ff420-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="ff420-114">(Wywołanie [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metody może wyemitować to liczba bajtów.)</span><span class="sxs-lookup"><span data-stu-id="ff420-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="ff420-115">Jeśli element wywołujący implementuje [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interfejsu (za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) lub [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` będzie wykonywać dwa przebiegi za pośrednictwem metadane do optymalizacji i skompresować je.</span><span class="sxs-lookup"><span data-stu-id="ff420-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="ff420-116">W przeciwnym razie są wykonywane nie optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="ff420-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="ff420-117">Jeśli będzie przeprowadzana Optymalizacja, Przekaż pierwszy po prostu sortuje struktur metadanych w celu dostrojenia wydajności wyszukiwań w trakcie importu.</span><span class="sxs-lookup"><span data-stu-id="ff420-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="ff420-118">Ten krok powoduje zwykle przenoszenie rekordy wokół, z efektem ubocznym, że tokeny zachowywane przez narzędzie do użytku w przyszłości są unieważnione.</span><span class="sxs-lookup"><span data-stu-id="ff420-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="ff420-119">Metadanych nie informuje wywołującego tokenu zmiany dopiero po drugim przebiegu, jednak.</span><span class="sxs-lookup"><span data-stu-id="ff420-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="ff420-120">W drugim przebiegu różne optymalizacje są wykonywane przeznaczonych do redukowania łącznego rozmiaru metadane, takie jak Optymalizacja zadań (wczesnego wiązania) `mdTypeRef` i `mdMemberRef` tokenów, gdy jest odwołanie do typu lub elementu członkowskiego, który jest zadeklarowana w bieżący zakres metadanych.</span><span class="sxs-lookup"><span data-stu-id="ff420-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="ff420-121">W tym przebiegu występuje round innego mapowania tokenu.</span><span class="sxs-lookup"><span data-stu-id="ff420-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="ff420-122">Po tym przebiegu aparat metadanych powiadamia wywołującego, za pośrednictwem jego `IMapToken` interfejsu dowolnego zmienić wartości tokenów.</span><span class="sxs-lookup"><span data-stu-id="ff420-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff420-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff420-123">Requirements</span></span>  
 <span data-ttu-id="ff420-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff420-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff420-125">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff420-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff420-126">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff420-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff420-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff420-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff420-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff420-128">See Also</span></span>  
 [<span data-ttu-id="ff420-129">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="ff420-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ff420-130">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ff420-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
