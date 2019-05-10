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
ms.openlocfilehash: 4afbe64979ec69a192af955400ca8f4118102bd4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665036"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="16796-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="16796-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="16796-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="16796-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="16796-104">Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="16796-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16796-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16796-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16796-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="16796-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="16796-107">[in] Wskaźnik do identyfikator GUID, który określa opcje, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="16796-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="16796-108">Zobacz sekcję Spostrzeżenia, aby listę obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="16796-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="16796-109">[out] Wartość zwrócona opcji.</span><span class="sxs-lookup"><span data-stu-id="16796-109">[out] The value of the returned option.</span></span> <span data-ttu-id="16796-110">Typ tej wartości będą wariant określoną opcję typu.</span><span class="sxs-lookup"><span data-stu-id="16796-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16796-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16796-111">Remarks</span></span>  
 <span data-ttu-id="16796-112">Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="16796-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="16796-113">Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="16796-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="16796-114">Jeśli `optionId` jest nie ma na tej liście, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując określono nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="16796-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="16796-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="16796-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="16796-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="16796-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="16796-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="16796-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="16796-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="16796-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="16796-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="16796-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="16796-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="16796-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="16796-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="16796-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16796-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16796-122">Requirements</span></span>  
 <span data-ttu-id="16796-123">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16796-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16796-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="16796-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16796-125">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16796-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16796-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16796-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16796-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16796-127">See also</span></span>

- [<span data-ttu-id="16796-128">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="16796-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="16796-129">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="16796-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
