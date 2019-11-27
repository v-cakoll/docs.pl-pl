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
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447916"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="5be44-102">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5be44-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="5be44-103">Rozszerza interfejs [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) przede wszystkim, aby zapewnić możliwość pracy z typami ogólnymi.</span><span class="sxs-lookup"><span data-stu-id="5be44-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5be44-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5be44-104">Methods</span></span>  
  
|<span data-ttu-id="5be44-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-105">Method</span></span>|<span data-ttu-id="5be44-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5be44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5be44-107">DefineGenericParam, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="5be44-108">Tworzy definicję parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="5be44-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="5be44-109">DefineMethodSpec, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="5be44-110">Tworzy wystąpienie ogólne metody i pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="5be44-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="5be44-111">GetDeltaSaveSize, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="5be44-112">Pobiera wartość wskazującą różnicę rozmiaru danych, które są wymagane do wyrażenia zmian w bieżącej sesji Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="5be44-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="5be44-113">ResetENCLog, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="5be44-114">Resetuje dziennik Edytuj i Kontynuuj i uruchamia nową sesję.</span><span class="sxs-lookup"><span data-stu-id="5be44-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="5be44-115">SaveDelta, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="5be44-116">Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="5be44-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="5be44-117">SaveDeltaToMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="5be44-118">Zapisuje zmiany z bieżącej sesji edycji i kontynuowania w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5be44-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="5be44-119">SaveDeltaToStream, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="5be44-120">Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="5be44-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="5be44-121">SetGenericParamProps, metoda</span><span class="sxs-lookup"><span data-stu-id="5be44-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="5be44-122">Ustawia wartości właściwości dla definicji parametru generycznego, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="5be44-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5be44-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5be44-123">Requirements</span></span>  
 <span data-ttu-id="5be44-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5be44-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5be44-125">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5be44-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5be44-126">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5be44-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5be44-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5be44-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be44-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5be44-128">See also</span></span>

- [<span data-ttu-id="5be44-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="5be44-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="5be44-130">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5be44-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
