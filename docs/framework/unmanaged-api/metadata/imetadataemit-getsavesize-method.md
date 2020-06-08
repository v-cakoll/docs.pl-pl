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
ms.openlocfilehash: 0a283c837e23ab1aafd3545df1dfe8a267de0557
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501290"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="de9a2-102">IMetaDataEmit::GetSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="de9a2-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="de9a2-103">Pobiera Szacowany rozmiar binarny zestawu i jego metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="de9a2-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de9a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de9a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de9a2-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="de9a2-106">podczas Wartość wyliczenia [CorSaveSize —](corsavesize-enumeration.md) , która określa, czy ma być pobierany dokładny czy przybliżony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="de9a2-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="de9a2-107">Prawidłowe są tylko trzy wartości: cssAccurate, cssQuick i cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="de9a2-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="de9a2-108">cssAccurate zwraca dokładny rozmiar zapisu, ale trwa dłużej.</span><span class="sxs-lookup"><span data-stu-id="de9a2-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="de9a2-109">cssQuick zwraca rozmiar, uzupełniony pod kątem bezpieczeństwa, ale zajmuje mniej czasu na obliczenia.</span><span class="sxs-lookup"><span data-stu-id="de9a2-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="de9a2-110">cssDiscardTransientCAs informuje `GetSaveSize` o tym, że może zgłosić atrybuty niestandardowe odrzucone.</span><span class="sxs-lookup"><span data-stu-id="de9a2-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="de9a2-111">określoną Wskaźnik do rozmiaru, który jest wymagany do zapisania pliku.</span><span class="sxs-lookup"><span data-stu-id="de9a2-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de9a2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de9a2-112">Remarks</span></span>  
 <span data-ttu-id="de9a2-113">`GetSaveSize`oblicza wymagane miejsce, w bajtach, do zapisania zestawu i wszystkich jego metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="de9a2-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="de9a2-114">(Wywołanie metody [IMetaDataEmit:: SaveToStream —](imetadataemit-savetostream-method.md) emituje tę liczbę bajtów).</span><span class="sxs-lookup"><span data-stu-id="de9a2-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="de9a2-115">Jeśli obiekt wywołujący implementuje interfejs [IMapToken](imaptoken-interface.md) (za pośrednictwem [IMetaDataEmit:: sethandleer](imetadataemit-sethandler-method.md) lub [IMetaDataEmit:: Merge](imetadataemit-merge-method.md)), `GetSaveSize` program wykona dwa przekazanie metadanych w celu optymalizacji i skompresowania.</span><span class="sxs-lookup"><span data-stu-id="de9a2-115">If the caller implements the [IMapToken](imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="de9a2-116">W przeciwnym razie optymalizacje nie są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="de9a2-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="de9a2-117">W przypadku przeprowadzania optymalizacji pierwsze przejście po prostu sortuje struktury metadanych w celu dostosowania wydajności wyszukiwania w czasie importu.</span><span class="sxs-lookup"><span data-stu-id="de9a2-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="de9a2-118">Ten krok zazwyczaj skutkuje przenoszeniem rekordów, a efektem ubocznym, które tokeny są przechowywane przez narzędzie do przyszłego odwołania, są unieważnione.</span><span class="sxs-lookup"><span data-stu-id="de9a2-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="de9a2-119">Metadane nie informują o tym, że wywołujący te zmiany tokenu są jednak do momentu drugiego przejścia.</span><span class="sxs-lookup"><span data-stu-id="de9a2-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="de9a2-120">W drugim przebiegu są wykonywane różne optymalizacje, które mają na celu zmniejszenie całkowitego rozmiaru metadanych, takich jak optymalizacja (wczesne wiązanie) `mdTypeRef` i `mdMemberRef` tokeny, gdy odwołanie dotyczy typu lub elementu członkowskiego, który jest zadeklarowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="de9a2-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="de9a2-121">W tym przebiegu występuje inne mapowanie tokenu.</span><span class="sxs-lookup"><span data-stu-id="de9a2-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="de9a2-122">Po tym przejściu aparat metadanych powiadamia obiekt wywołujący `IMapToken` o wszystkich zmienionych wartościach tokenu za pomocą interfejsu.</span><span class="sxs-lookup"><span data-stu-id="de9a2-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de9a2-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de9a2-123">Requirements</span></span>  
 <span data-ttu-id="de9a2-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de9a2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de9a2-125">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="de9a2-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de9a2-126">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="de9a2-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de9a2-127">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de9a2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9a2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de9a2-128">See also</span></span>

- [<span data-ttu-id="de9a2-129">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="de9a2-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="de9a2-130">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="de9a2-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
