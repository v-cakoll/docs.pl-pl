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
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177719"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="59491-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="59491-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="59491-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="59491-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="59491-104">Opcja określa sposób obsługi wywołań bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="59491-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59491-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59491-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59491-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59491-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="59491-107">[w] Wskaźnik do identyfikatora GUID, który określa opcję do pobrania.</span><span class="sxs-lookup"><span data-stu-id="59491-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="59491-108">Zobacz sekcję Uwagi, aby uzyskać listę obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="59491-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="59491-109">[na zewnątrz] Wartość zwróconej opcji.</span><span class="sxs-lookup"><span data-stu-id="59491-109">[out] The value of the returned option.</span></span> <span data-ttu-id="59491-110">Typ tej wartości będzie wariantem typu określonej opcji.</span><span class="sxs-lookup"><span data-stu-id="59491-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59491-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59491-111">Remarks</span></span>  
 <span data-ttu-id="59491-112">Na poniższej liście przedstawiono identyfikatory GUID, które są obsługiwane dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="59491-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="59491-113">Opisy można znaleźć w pliku [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)</span><span class="sxs-lookup"><span data-stu-id="59491-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="59491-114">Jeśli `optionId` nie ma tej listy, ta `E_INVALIDARG`metoda zwraca HRESULT , wskazując niepoprawny parametr.</span><span class="sxs-lookup"><span data-stu-id="59491-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="59491-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="59491-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="59491-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="59491-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="59491-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="59491-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="59491-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="59491-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="59491-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="59491-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="59491-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="59491-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="59491-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="59491-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59491-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59491-122">Requirements</span></span>  
 <span data-ttu-id="59491-123">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59491-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59491-124">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="59491-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59491-125">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59491-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59491-126">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59491-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59491-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59491-127">See also</span></span>

- [<span data-ttu-id="59491-128">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="59491-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="59491-129">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="59491-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
