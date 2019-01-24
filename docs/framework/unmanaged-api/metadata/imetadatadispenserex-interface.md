---
title: IMetaDataDispenserEx — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4fa4830756ee6ac896611dbc243207739151d3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547322"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="d818f-102">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d818f-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="d818f-103">Rozszerza [imetadatadispenser — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interfejsu, aby zapewnić możliwość kontrolowania, jak działają metadanych interfejsów API w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="d818f-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d818f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d818f-104">Methods</span></span>  
  
|<span data-ttu-id="d818f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-105">Method</span></span>|<span data-ttu-id="d818f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d818f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d818f-107">FindAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="d818f-108">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="d818f-108">This method is not implemented.</span></span> <span data-ttu-id="d818f-109">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d818f-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d818f-110">FindAssemblyModule, metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="d818f-111">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="d818f-111">This method is not implemented.</span></span> <span data-ttu-id="d818f-112">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d818f-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d818f-113">GetCORSystemDirectory, metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="d818f-114">Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d818f-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="d818f-115">Ta metoda jest obsługiwana tylko do użytku przez debugery spoza procesu.</span><span class="sxs-lookup"><span data-stu-id="d818f-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="d818f-116">Wywoływana z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d818f-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d818f-117">GetOption, metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="d818f-118">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d818f-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="d818f-119">Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d818f-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="d818f-120">OpenScopeOnITypeInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="d818f-121">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="d818f-121">This method is not implemented.</span></span> <span data-ttu-id="d818f-122">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d818f-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="d818f-123">SetOption, metoda</span><span class="sxs-lookup"><span data-stu-id="d818f-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="d818f-124">Ustawia określoną opcję do podanej wartości w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="d818f-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="d818f-125">Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d818f-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d818f-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d818f-126">Requirements</span></span>  
 <span data-ttu-id="d818f-127">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d818f-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d818f-128">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d818f-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d818f-129">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d818f-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d818f-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d818f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d818f-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d818f-131">See also</span></span>
- [<span data-ttu-id="d818f-132">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="d818f-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="d818f-133">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="d818f-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="d818f-134">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="d818f-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d818f-135">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d818f-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
