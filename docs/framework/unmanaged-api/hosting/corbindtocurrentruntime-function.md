---
title: CorBindToCurrentRuntime — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138317"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="1c7ba-102">CorBindToCurrentRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1c7ba-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="1c7ba-103">Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji przechowywanych w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="1c7ba-104">Format pliku XML jest modelowany po standardowym pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="1c7ba-105">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="1c7ba-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="1c7ba-106">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="1c7ba-107">Zobacz [ładowanie środowiska uruchomieniowego języka wspólnego do procesu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1c7ba-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c7ba-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c7ba-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c7ba-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c7ba-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="1c7ba-110">podczas Nazwa pliku konfiguracji aplikacji, który określa wersję środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="1c7ba-111">Jeśli nazwa pliku nie jest w pełni kwalifikowana, zakłada się, że znajduje się w tym samym katalogu co plik wykonywalny wywołujący wywołanie.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="1c7ba-112">Wersja środowiska uruchomieniowego do załadowania jest opisana przez atrybut Version w [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="1c7ba-113">Jeśli nie określono żadnej wersji lub nie można znaleźć elementu `<requiredRuntime>`, zostanie załadowana Najnowsza wersja środowiska CLR zainstalowana na maszynie.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="1c7ba-114">podczas `CLSID` klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1c7ba-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="1c7ba-115">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="1c7ba-116">podczas `IID` żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="1c7ba-117">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="1c7ba-118">określoną Zwrócony wskaźnik interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c7ba-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c7ba-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c7ba-119">Requirements</span></span>  
 <span data-ttu-id="1c7ba-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c7ba-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c7ba-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c7ba-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c7ba-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c7ba-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c7ba-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c7ba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7ba-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c7ba-124">See also</span></span>

- [<span data-ttu-id="1c7ba-125">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="1c7ba-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="1c7ba-126">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="1c7ba-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="1c7ba-127">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="1c7ba-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="1c7ba-128">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="1c7ba-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="1c7ba-129">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c7ba-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="1c7ba-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1c7ba-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
