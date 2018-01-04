---
title: "IMetaDataDispenserEx — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cf062029647d4834118a459db378c8535182daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="dccf0-102">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dccf0-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="dccf0-103">Rozszerza [IMetaDataDispenser — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interfejsu możliwości, aby kontrolować sposób działania metadanych interfejsów API w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="dccf0-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dccf0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dccf0-104">Methods</span></span>  
  
|<span data-ttu-id="dccf0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-105">Method</span></span>|<span data-ttu-id="dccf0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dccf0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dccf0-107">FindAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="dccf0-108">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="dccf0-108">This method is not implemented.</span></span> <span data-ttu-id="dccf0-109">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dccf0-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="dccf0-110">FindAssemblyModule, metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="dccf0-111">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="dccf0-111">This method is not implemented.</span></span> <span data-ttu-id="dccf0-112">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dccf0-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="dccf0-113">GetCORSystemDirectory, metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="dccf0-114">Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="dccf0-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="dccf0-115">Ta metoda jest obsługiwana tylko przez debugery poza procesem.</span><span class="sxs-lookup"><span data-stu-id="dccf0-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="dccf0-116">Wywoływane z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dccf0-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="dccf0-117">GetOption, metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="dccf0-118">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="dccf0-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="dccf0-119">Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="dccf0-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="dccf0-120">OpenScopeOnITypeInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="dccf0-121">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="dccf0-121">This method is not implemented.</span></span> <span data-ttu-id="dccf0-122">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dccf0-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="dccf0-123">SetOption, metoda</span><span class="sxs-lookup"><span data-stu-id="dccf0-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="dccf0-124">Ustawia określoną opcję do podanej wartości w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="dccf0-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="dccf0-125">Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="dccf0-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dccf0-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dccf0-126">Requirements</span></span>  
 <span data-ttu-id="dccf0-127">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dccf0-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dccf0-128">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dccf0-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dccf0-129">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dccf0-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dccf0-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dccf0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccf0-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dccf0-131">See Also</span></span>  
 [<span data-ttu-id="dccf0-132">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="dccf0-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="dccf0-133">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="dccf0-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="dccf0-134">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="dccf0-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dccf0-135">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="dccf0-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
