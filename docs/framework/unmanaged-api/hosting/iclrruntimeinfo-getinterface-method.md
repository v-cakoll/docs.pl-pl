---
title: ICLRRuntimeInfo::GetInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771764"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="bc9ad-102">ICLRRuntimeInfo::GetInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc9ad-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="bc9ad-103">Ładuje środowisko CLR do bieżący proces i zwraca środowiska uruchomieniowego, wskaźniki interfejsu, takich jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), i [imetadatadispenserex —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bc9ad-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="bc9ad-104">Ta metoda zastępuje wszystkie `CorBindTo`\* funkcje w [przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc9ad-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc9ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc9ad-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="bc9ad-107">[in] Interfejs CLSID dla klasy coclass.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="bc9ad-108">[in] Identyfikatorem IID żądany `rclsid` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="bc9ad-109">[out] Wskaźnik do interfejsu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc9ad-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc9ad-110">Return Value</span></span>  
 <span data-ttu-id="bc9ad-111">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bc9ad-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc9ad-112">HRESULT</span></span>|<span data-ttu-id="bc9ad-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bc9ad-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc9ad-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc9ad-114">S_OK</span></span>|<span data-ttu-id="bc9ad-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="bc9ad-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bc9ad-116">E_POINTER</span></span>|<span data-ttu-id="bc9ad-117">`ppUnk` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="bc9ad-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bc9ad-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bc9ad-119">Nie ma wystarczającej ilości pamięci dostępnej może obsłużyć żądania.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="bc9ad-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="bc9ad-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="bc9ad-121">Środowiskiem uruchomieniowym w różnych była już powiązana starsze zasady 2 aktywacji wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9ad-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc9ad-122">Remarks</span></span>  
 <span data-ttu-id="bc9ad-123">Ta metoda powoduje, że CLR do załadowane, ale nie zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="bc9ad-124">W poniższej tabeli przedstawiono obsługiwane kombinacje w celach `rclsid` i `riid`.</span><span class="sxs-lookup"><span data-stu-id="bc9ad-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="bc9ad-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="bc9ad-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="bc9ad-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="bc9ad-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="bc9ad-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="bc9ad-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="bc9ad-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="bc9ad-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="bc9ad-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bc9ad-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="bc9ad-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bc9ad-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="bc9ad-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bc9ad-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="bc9ad-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bc9ad-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="bc9ad-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="bc9ad-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="bc9ad-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="bc9ad-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="bc9ad-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="bc9ad-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="bc9ad-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="bc9ad-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="bc9ad-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bc9ad-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="bc9ad-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bc9ad-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc9ad-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc9ad-139">Requirements</span></span>  
 <span data-ttu-id="bc9ad-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9ad-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9ad-141">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bc9ad-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bc9ad-142">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc9ad-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc9ad-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9ad-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9ad-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc9ad-144">See also</span></span>

- [<span data-ttu-id="bc9ad-145">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc9ad-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="bc9ad-146">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc9ad-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="bc9ad-147">Hosting</span><span class="sxs-lookup"><span data-stu-id="bc9ad-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
