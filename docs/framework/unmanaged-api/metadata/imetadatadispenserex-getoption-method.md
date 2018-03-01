---
title: "IMetaDataDispenserEx::GetOption — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1fd59fa20e95de8486eaa7f18a63333459361ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="2e8e3-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e8e3-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="2e8e3-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="2e8e3-104">Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8e3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e8e3-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e8e3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e8e3-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="2e8e3-107">[in] Wskaźnik do identyfikatora GUID, który określa opcje, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="2e8e3-108">Zobacz sekcję uwag listę obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2e8e3-109">[out] Wartości zwracane opcji.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-109">[out] The value of the returned option.</span></span> <span data-ttu-id="2e8e3-110">Typ tej wartości będą wariant opcji określonego typu.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e8e3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e8e3-111">Remarks</span></span>  
 <span data-ttu-id="2e8e3-112">Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="2e8e3-113">Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="2e8e3-114">Jeśli `optionId` jest spoza tej listy, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="2e8e3-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="2e8e3-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="2e8e3-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="2e8e3-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="2e8e3-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="2e8e3-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="2e8e3-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="2e8e3-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="2e8e3-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="2e8e3-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="2e8e3-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="2e8e3-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="2e8e3-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="2e8e3-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="2e8e3-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e8e3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e8e3-122">Requirements</span></span>  
 <span data-ttu-id="2e8e3-123">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e8e3-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e8e3-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e8e3-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e8e3-125">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e8e3-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e8e3-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e8e3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8e3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e8e3-127">See Also</span></span>  
 [<span data-ttu-id="2e8e3-128">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e8e3-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="2e8e3-129">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e8e3-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
