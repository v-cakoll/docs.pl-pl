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
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431145"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="ab2b7-102">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab2b7-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="ab2b7-103">Rozszerza interfejs [interfejsu IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) , aby zapewnić możliwość sterowania sposobem działania interfejsów API metadanych w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab2b7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab2b7-104">Methods</span></span>  
  
|<span data-ttu-id="ab2b7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-105">Method</span></span>|<span data-ttu-id="ab2b7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ab2b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab2b7-107">FindAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="ab2b7-108">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-108">This method is not implemented.</span></span> <span data-ttu-id="ab2b7-109">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ab2b7-110">FindAssemblyModule, metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="ab2b7-111">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-111">This method is not implemented.</span></span> <span data-ttu-id="ab2b7-112">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ab2b7-113">GetCORSystemDirectory, metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="ab2b7-114">Pobiera katalog, który przechowuje bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ab2b7-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="ab2b7-115">Ta metoda jest obsługiwana tylko dla debugerów out-of-process.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="ab2b7-116">Jeśli wywoływana z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ab2b7-117">GetOption, metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="ab2b7-118">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="ab2b7-119">Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="ab2b7-120">OpenScopeOnITypeInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="ab2b7-121">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-121">This method is not implemented.</span></span> <span data-ttu-id="ab2b7-122">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ab2b7-123">SetOption, metoda</span><span class="sxs-lookup"><span data-stu-id="ab2b7-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="ab2b7-124">Ustawia określoną opcję na daną wartość dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="ab2b7-125">Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab2b7-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab2b7-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab2b7-126">Requirements</span></span>  
 <span data-ttu-id="ab2b7-127">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab2b7-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab2b7-128">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ab2b7-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab2b7-129">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ab2b7-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab2b7-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2b7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2b7-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab2b7-131">See also</span></span>

- [<span data-ttu-id="ab2b7-132">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="ab2b7-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ab2b7-133">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab2b7-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="ab2b7-134">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab2b7-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ab2b7-135">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab2b7-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
