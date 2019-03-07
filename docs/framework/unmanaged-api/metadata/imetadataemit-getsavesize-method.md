---
title: IMetaDataEmit::GetSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16984fe108abd1cfc01c471bcfc091a805b28e83
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501506"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="65eff-102">IMetaDataEmit::GetSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="65eff-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="65eff-103">Szacowany rozmiar binarne zestawu i jego metadane są pobierane w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="65eff-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65eff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65eff-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65eff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65eff-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="65eff-106">[in] Wartość [corsavesize —](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wyliczenie, które określa, czy uzyskać dokładne lub Przybliżony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="65eff-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="65eff-107">Tylko dla trzech wartości są prawidłowe: cssAccurate, cssQuick i cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="65eff-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="65eff-108">cssAccurate zwraca dokładnie Zapisz rozmiar, ale trwa dłużej do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="65eff-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="65eff-109">cssQuick zwraca rozmiar, uzupełniona na potrzeby bezpieczeństwa, ale zajmuje mniej czasu, aby obliczyć.</span><span class="sxs-lookup"><span data-stu-id="65eff-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="65eff-110">informuje cssDiscardTransientCAs `GetSaveSize` , może ona zgłosić natychmiast discardable atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="65eff-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="65eff-111">[out] Wskaźnik do rozmiaru który jest wymagany, aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="65eff-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65eff-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65eff-112">Remarks</span></span>  
 <span data-ttu-id="65eff-113">`GetSaveSize` Obliczanie miejsca wymaganego w bajtach, można zapisać zestawu i wszystkich jego metadane w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="65eff-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="65eff-114">(Po wywołaniu [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metoda może emitować to liczba bajtów.)</span><span class="sxs-lookup"><span data-stu-id="65eff-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="65eff-115">Jeśli obiekt wywołujący implementuje [imaptoken —](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interfejsu (za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) lub [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` wykona dwa przebiegi za pośrednictwem metadane do optymalizacji i skompresować je.</span><span class="sxs-lookup"><span data-stu-id="65eff-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="65eff-116">W przeciwnym razie są wykonywane nie optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="65eff-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="65eff-117">Jeśli będzie przeprowadzana Optymalizacja, pierwszym przebiegu po prostu sortuje struktur metadanych, aby dostosować wydajność wyszukiwania w trakcie importu.</span><span class="sxs-lookup"><span data-stu-id="65eff-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="65eff-118">Zazwyczaj ten krok powoduje przeniesienie rekordów wokół, za pomocą efekt uboczny, że tokeny zachowywane przez narzędzie do użytku w przyszłości nie są unieważniane.</span><span class="sxs-lookup"><span data-stu-id="65eff-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="65eff-119">Metadane nie informuje obiekt wywołujący o tych zmianach token aż do po drugim — dostęp próbny, jednak.</span><span class="sxs-lookup"><span data-stu-id="65eff-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="65eff-120">W drugim przebiegu, wykonywane są różne optymalizacje, które są przeznaczone do redukowania łącznego rozmiaru metadane, takie jak Optymalizacja odkładania (wczesne powiązania) `mdTypeRef` i `mdMemberRef` tokenów w przypadku odwołania do typu lub elementu członkowskiego, które są zadeklarowane w bieżący zakres metadanych.</span><span class="sxs-lookup"><span data-stu-id="65eff-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="65eff-121">W tym przebiegu kolejną porcję tokenu mapowanie występuje.</span><span class="sxs-lookup"><span data-stu-id="65eff-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="65eff-122">Po tym przebiegu aparatu metadanych powiadamia obiekt wywołujący, za pośrednictwem jego `IMapToken` interfejsu dowolnego zmienione wartości tokenu.</span><span class="sxs-lookup"><span data-stu-id="65eff-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65eff-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65eff-123">Requirements</span></span>  
 <span data-ttu-id="65eff-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65eff-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65eff-125">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="65eff-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65eff-126">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65eff-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65eff-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65eff-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65eff-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65eff-128">See also</span></span>
- [<span data-ttu-id="65eff-129">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="65eff-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="65eff-130">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="65eff-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
