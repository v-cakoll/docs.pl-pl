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
ms.openlocfilehash: a117fcdf2ba9d37fb5483cc85fb575e5d3476794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447677"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="15a14-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="15a14-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="15a14-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="15a14-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="15a14-104">Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="15a14-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a14-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15a14-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15a14-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="15a14-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="15a14-107">[in] Wskaźnik do identyfikatora GUID, który określa opcje, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="15a14-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="15a14-108">Zobacz sekcję uwag listę obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="15a14-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="15a14-109">[out] Wartości zwracane opcji.</span><span class="sxs-lookup"><span data-stu-id="15a14-109">[out] The value of the returned option.</span></span> <span data-ttu-id="15a14-110">Typ tej wartości będą wariant opcji określonego typu.</span><span class="sxs-lookup"><span data-stu-id="15a14-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15a14-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15a14-111">Remarks</span></span>  
 <span data-ttu-id="15a14-112">Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="15a14-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="15a14-113">Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="15a14-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="15a14-114">Jeśli `optionId` jest spoza tej listy, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="15a14-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="15a14-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="15a14-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="15a14-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="15a14-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="15a14-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="15a14-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="15a14-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="15a14-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="15a14-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="15a14-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="15a14-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="15a14-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="15a14-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="15a14-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a14-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15a14-122">Requirements</span></span>  
 <span data-ttu-id="15a14-123">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a14-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a14-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15a14-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15a14-125">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15a14-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15a14-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a14-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a14-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a14-127">See Also</span></span>  
 [<span data-ttu-id="15a14-128">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="15a14-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="15a14-129">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="15a14-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
