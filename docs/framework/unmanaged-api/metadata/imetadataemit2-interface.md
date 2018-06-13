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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 418e5287852b1a8d69d310d2ba71e4f2a3b5d7bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449234"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="0a296-102">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0a296-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="0a296-103">Rozszerza [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejsu głównie, aby zapewnić możliwość korzystania z typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="0a296-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a296-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0a296-104">Methods</span></span>  
  
|<span data-ttu-id="0a296-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-105">Method</span></span>|<span data-ttu-id="0a296-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0a296-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a296-107">DefineGenericParam, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="0a296-108">Tworzy definicję dla parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0a296-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="0a296-109">DefineMethodSpec, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="0a296-110">Tworzy wystąpienie ogólnego metody i pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="0a296-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="0a296-111">GetDeltaSaveSize, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="0a296-112">Pobiera wartość wskazującą różnica w rozmiarze danych, który jest wymagany do express zmiany w bieżącej sesji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="0a296-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="0a296-113">ResetENCLog, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="0a296-114">Resetuje dziennika edit-and-continue i rozpoczęcie nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="0a296-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="0a296-115">SaveDelta, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="0a296-116">Zapisuje zmiany z bieżącej sesji edit-and-continue do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="0a296-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="0a296-117">SaveDeltaToMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="0a296-118">Zapisuje zmiany z bieżącej sesji edit-and-continue pamięci.</span><span class="sxs-lookup"><span data-stu-id="0a296-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="0a296-119">SaveDeltaToStream, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="0a296-120">Zapisuje zmiany z bieżącej sesji edit-and-continue określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="0a296-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="0a296-121">SetGenericParamProps, metoda</span><span class="sxs-lookup"><span data-stu-id="0a296-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="0a296-122">Ustawia wartości właściwości dla definicji parametru ogólnego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="0a296-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a296-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a296-123">Requirements</span></span>  
 <span data-ttu-id="0a296-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a296-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a296-125">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0a296-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a296-126">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a296-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a296-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a296-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a296-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a296-128">See Also</span></span>  
 [<span data-ttu-id="0a296-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="0a296-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="0a296-130">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a296-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
