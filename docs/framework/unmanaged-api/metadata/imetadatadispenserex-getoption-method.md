---
title: IMetaDataDispenserEx::GetOption — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe9bc9aea4ceb0f5b5c03416f43894b482c3294e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136633"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="5b3a7-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b3a7-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="5b3a7-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="5b3a7-104">Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3a7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b3a7-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b3a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b3a7-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="5b3a7-107">[in] Wskaźnik do identyfikator GUID, który określa opcje, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="5b3a7-108">Zobacz sekcję Spostrzeżenia, aby listę obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5b3a7-109">[out] Wartość zwrócona opcji.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-109">[out] The value of the returned option.</span></span> <span data-ttu-id="5b3a7-110">Typ tej wartości będą wariant określoną opcję typu.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3a7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b3a7-111">Remarks</span></span>  
 <span data-ttu-id="5b3a7-112">Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="5b3a7-113">Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="5b3a7-114">Jeśli `optionId` jest nie ma na tej liście, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując określono nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="5b3a7-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="5b3a7-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="5b3a7-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="5b3a7-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="5b3a7-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="5b3a7-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="5b3a7-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="5b3a7-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="5b3a7-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="5b3a7-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="5b3a7-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="5b3a7-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="5b3a7-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="5b3a7-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="5b3a7-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b3a7-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b3a7-122">Requirements</span></span>  
 <span data-ttu-id="5b3a7-123">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b3a7-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b3a7-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5b3a7-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b3a7-125">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b3a7-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5b3a7-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5b3a7-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b3a7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b3a7-127">See also</span></span>

- [<span data-ttu-id="5b3a7-128">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5b3a7-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="5b3a7-129">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5b3a7-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
