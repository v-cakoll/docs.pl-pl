---
title: "ICorRuntimeHost::GetConfiguration — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c0a95df2140d2eaf771fcd8f50cd733b9133e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="09562-102">ICorRuntimeHost::GetConfiguration — Metoda</span><span class="sxs-lookup"><span data-stu-id="09562-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="09562-103">Pobiera obiekt, który umożliwia hosta określić konfigurację wywołania zwrotnego środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="09562-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09562-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09562-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09562-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09562-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="09562-106">[out] Wskaźnik do adresu [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) obiektu, który może służyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="09562-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09562-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09562-107">Remarks</span></span>  
 <span data-ttu-id="09562-108">Przed jego inicjowania; należy skonfigurować środowisko CLR w przeciwnym razie `GetConfiguration` metoda zwróci wartość HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="09562-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09562-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09562-109">Requirements</span></span>  
 <span data-ttu-id="09562-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09562-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09562-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09562-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09562-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09562-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09562-113">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="09562-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09562-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09562-114">See Also</span></span>  
 [<span data-ttu-id="09562-115">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="09562-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
