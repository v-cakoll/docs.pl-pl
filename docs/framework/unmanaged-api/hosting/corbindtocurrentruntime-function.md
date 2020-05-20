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
ms.openlocfilehash: 348ca9d157a668dcd180076475f1fe9861197174
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616676"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="14cfe-102">CorBindToCurrentRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="14cfe-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="14cfe-103">Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji przechowywanych w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="14cfe-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="14cfe-104">Format pliku XML jest modelowany po standardowym pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14cfe-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="14cfe-105">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="14cfe-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="14cfe-106">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="14cfe-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="14cfe-107">Zobacz [ładowanie środowiska uruchomieniowego języka wspólnego do procesu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="14cfe-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14cfe-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="14cfe-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14cfe-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="14cfe-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="14cfe-110">podczas Nazwa pliku konfiguracji aplikacji, który określa wersję środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="14cfe-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="14cfe-111">Jeśli nazwa pliku nie jest w pełni kwalifikowana, zakłada się, że znajduje się w tym samym katalogu co plik wykonywalny wywołujący wywołanie.</span><span class="sxs-lookup"><span data-stu-id="14cfe-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="14cfe-112">Wersja środowiska uruchomieniowego do załadowania jest opisana przez atrybut Version w elemencie [ \< requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="14cfe-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="14cfe-113">Jeśli nie określono żadnej wersji lub `<requiredRuntime>` nie można znaleźć elementu, zostanie załadowana Najnowsza wersja środowiska CLR, która jest zainstalowana na maszynie.</span><span class="sxs-lookup"><span data-stu-id="14cfe-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="14cfe-114">podczas `CLSID`Klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="14cfe-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="14cfe-115">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="14cfe-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="14cfe-116">podczas Żądanego `IID` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="14cfe-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="14cfe-117">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="14cfe-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="14cfe-118">określoną Zwrócony wskaźnik interfejsu.</span><span class="sxs-lookup"><span data-stu-id="14cfe-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14cfe-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14cfe-119">Requirements</span></span>  
 <span data-ttu-id="14cfe-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14cfe-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14cfe-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="14cfe-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14cfe-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="14cfe-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14cfe-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14cfe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14cfe-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14cfe-124">See also</span></span>

- [<span data-ttu-id="14cfe-125">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="14cfe-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="14cfe-126">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="14cfe-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="14cfe-127">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="14cfe-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="14cfe-128">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="14cfe-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="14cfe-129">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="14cfe-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="14cfe-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="14cfe-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
