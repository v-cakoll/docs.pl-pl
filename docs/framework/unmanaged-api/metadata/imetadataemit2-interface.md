---
title: IMetaDataEmit2 — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493044"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="3582f-102">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3582f-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="3582f-103">Rozszerza interfejs [IMetaDataEmit](imetadataemit-interface.md) przede wszystkim, aby zapewnić możliwość pracy z typami ogólnymi.</span><span class="sxs-lookup"><span data-stu-id="3582f-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3582f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3582f-104">Methods</span></span>  
  
|<span data-ttu-id="3582f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-105">Method</span></span>|<span data-ttu-id="3582f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3582f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3582f-107">DefineGenericParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="3582f-108">Tworzy definicję parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3582f-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="3582f-109">DefineMethodSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="3582f-110">Tworzy wystąpienie ogólne metody i pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="3582f-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="3582f-111">GetDeltaSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="3582f-112">Pobiera wartość wskazującą różnicę rozmiaru danych, które są wymagane do wyrażenia zmian w bieżącej sesji Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="3582f-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="3582f-113">ResetENCLog — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="3582f-114">Resetuje dziennik Edytuj i Kontynuuj i uruchamia nową sesję.</span><span class="sxs-lookup"><span data-stu-id="3582f-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="3582f-115">SaveDelta — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="3582f-116">Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="3582f-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="3582f-117">SaveDeltaToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="3582f-118">Zapisuje zmiany z bieżącej sesji edycji i kontynuowania w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3582f-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="3582f-119">SaveDeltaToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="3582f-120">Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="3582f-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="3582f-121">SetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="3582f-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="3582f-122">Ustawia wartości właściwości dla definicji parametru generycznego, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="3582f-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3582f-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3582f-123">Requirements</span></span>  
 <span data-ttu-id="3582f-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3582f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3582f-125">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3582f-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3582f-126">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3582f-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3582f-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3582f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3582f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3582f-128">See also</span></span>

- [<span data-ttu-id="3582f-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="3582f-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="3582f-130">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3582f-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
