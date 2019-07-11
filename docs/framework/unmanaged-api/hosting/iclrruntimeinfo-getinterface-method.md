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
ms.openlocfilehash: 4244ef04d6789b7c17ccc8330cb0c26a6c9f3866
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765547"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="07c8f-102">ICLRRuntimeInfo::GetInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="07c8f-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="07c8f-103">Ładuje środowisko CLR do bieżący proces i zwraca środowiska uruchomieniowego, wskaźniki interfejsu, takich jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), i [imetadatadispenserex —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="07c8f-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="07c8f-104">Ta metoda zastępuje wszystkie `CorBindTo`\* funkcje w [przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="07c8f-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07c8f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="07c8f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07c8f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="07c8f-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="07c8f-107">[in] Interfejs CLSID dla klasy coclass.</span><span class="sxs-lookup"><span data-stu-id="07c8f-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="07c8f-108">[in] Identyfikatorem IID żądany `rclsid` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="07c8f-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="07c8f-109">[out] Wskaźnik do interfejsu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="07c8f-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07c8f-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="07c8f-110">Return Value</span></span>  
 <span data-ttu-id="07c8f-111">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="07c8f-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="07c8f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07c8f-112">HRESULT</span></span>|<span data-ttu-id="07c8f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="07c8f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07c8f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="07c8f-114">S_OK</span></span>|<span data-ttu-id="07c8f-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="07c8f-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="07c8f-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="07c8f-116">E_POINTER</span></span>|<span data-ttu-id="07c8f-117">`ppUnk` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="07c8f-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="07c8f-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="07c8f-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="07c8f-119">Nie ma wystarczającej ilości pamięci dostępnej może obsłużyć żądania.</span><span class="sxs-lookup"><span data-stu-id="07c8f-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="07c8f-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="07c8f-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="07c8f-121">Środowiskiem uruchomieniowym w różnych była już powiązana starsze zasady 2 aktywacji wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="07c8f-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07c8f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07c8f-122">Remarks</span></span>  
 <span data-ttu-id="07c8f-123">Ta metoda powoduje, że CLR do załadowane, ale nie zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="07c8f-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="07c8f-124">W poniższej tabeli przedstawiono obsługiwane kombinacje w celach `rclsid` i `riid`.</span><span class="sxs-lookup"><span data-stu-id="07c8f-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="07c8f-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="07c8f-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="07c8f-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="07c8f-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="07c8f-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="07c8f-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="07c8f-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="07c8f-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="07c8f-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="07c8f-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="07c8f-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="07c8f-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="07c8f-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="07c8f-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="07c8f-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="07c8f-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="07c8f-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="07c8f-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="07c8f-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="07c8f-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="07c8f-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="07c8f-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="07c8f-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="07c8f-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="07c8f-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="07c8f-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="07c8f-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="07c8f-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07c8f-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07c8f-139">Requirements</span></span>  
 <span data-ttu-id="07c8f-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07c8f-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c8f-141">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="07c8f-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="07c8f-142">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07c8f-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07c8f-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07c8f-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c8f-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07c8f-144">See also</span></span>

- [<span data-ttu-id="07c8f-145">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="07c8f-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="07c8f-146">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="07c8f-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="07c8f-147">Hosting</span><span class="sxs-lookup"><span data-stu-id="07c8f-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
