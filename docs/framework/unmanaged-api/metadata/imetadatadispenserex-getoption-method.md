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
ms.openlocfilehash: 5512c503d8b4048c613ab88c2b4d9d19cdbb9dca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479037"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="592aa-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="592aa-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="592aa-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="592aa-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="592aa-104">Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="592aa-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="592aa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="592aa-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="592aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="592aa-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="592aa-107">[in] Wskaźnik do identyfikator GUID, który określa opcje, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="592aa-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="592aa-108">Zobacz sekcję Spostrzeżenia, aby listę obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="592aa-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="592aa-109">[out] Wartość zwrócona opcji.</span><span class="sxs-lookup"><span data-stu-id="592aa-109">[out] The value of the returned option.</span></span> <span data-ttu-id="592aa-110">Typ tej wartości będą wariant określoną opcję typu.</span><span class="sxs-lookup"><span data-stu-id="592aa-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="592aa-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="592aa-111">Remarks</span></span>  
 <span data-ttu-id="592aa-112">Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="592aa-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="592aa-113">Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="592aa-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="592aa-114">Jeśli `optionId` jest nie ma na tej liście, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując określono nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="592aa-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="592aa-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="592aa-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="592aa-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="592aa-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="592aa-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="592aa-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="592aa-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="592aa-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="592aa-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="592aa-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="592aa-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="592aa-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="592aa-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="592aa-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="592aa-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="592aa-122">Requirements</span></span>  
 <span data-ttu-id="592aa-123">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="592aa-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="592aa-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="592aa-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="592aa-125">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="592aa-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="592aa-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="592aa-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592aa-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="592aa-127">See also</span></span>
- [<span data-ttu-id="592aa-128">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="592aa-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="592aa-129">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="592aa-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
