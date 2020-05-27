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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008784"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="86f74-102">IMetaDataDispenserEx::GetOption — Metoda</span><span class="sxs-lookup"><span data-stu-id="86f74-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="86f74-103">Pobiera wartość określonej opcji dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="86f74-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="86f74-104">Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="86f74-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f74-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="86f74-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86f74-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="86f74-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="86f74-107">podczas Wskaźnik do identyfikatora GUID, który określa opcję do pobrania.</span><span class="sxs-lookup"><span data-stu-id="86f74-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="86f74-108">Zobacz sekcję Uwagi, aby zapoznać się z listą obsługiwanych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="86f74-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="86f74-109">określoną Wartość zwracanej opcji.</span><span class="sxs-lookup"><span data-stu-id="86f74-109">[out] The value of the returned option.</span></span> <span data-ttu-id="86f74-110">Typ tej wartości będzie wariantem typu określonej opcji.</span><span class="sxs-lookup"><span data-stu-id="86f74-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f74-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86f74-111">Remarks</span></span>  
 <span data-ttu-id="86f74-112">Poniższa lista zawiera identyfikatory GUID, które są obsługiwane dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="86f74-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="86f74-113">Aby uzyskać opis, zobacz metodę [IMetaDataDispenserEx:: SetOption](imetadatadispenserex-setoption-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86f74-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="86f74-114">Jeśli `optionId` nie znajduje się na tej liście, ta metoda zwraca wartość HRESULT `E_INVALIDARG` , wskazującą nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="86f74-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="86f74-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="86f74-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="86f74-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="86f74-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="86f74-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="86f74-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="86f74-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="86f74-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="86f74-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="86f74-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="86f74-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="86f74-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="86f74-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="86f74-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f74-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86f74-122">Requirements</span></span>  
 <span data-ttu-id="86f74-123">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f74-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f74-124">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="86f74-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86f74-125">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86f74-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86f74-126">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f74-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f74-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86f74-127">See also</span></span>

- [<span data-ttu-id="86f74-128">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="86f74-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="86f74-129">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86f74-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
