---
title: CorExitProcess — Funkcja
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: fe61503cdf46b6b2cf568deb78b96f8fa885c203
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136931"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="bd464-102">CorExitProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bd464-102">CorExitProcess Function</span></span>
<span data-ttu-id="bd464-103">Zamyka bieżący proces niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="bd464-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="bd464-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bd464-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="bd464-105">Zamiast tego użyj metody [ICLRMetaHost:: ExitProcess —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bd464-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd464-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd464-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd464-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd464-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="bd464-108">Liczba całkowita, która określa kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="bd464-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd464-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd464-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd464-110">Począwszy od .NET Framework 4, `CorExitProcess` opuszcza każde uruchomione środowisko uruchomieniowe w procesie, a nie tylko środowisko uruchomieniowe, do którego zostały powiązane starsze interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="bd464-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd464-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd464-111">Requirements</span></span>  
 <span data-ttu-id="bd464-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd464-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd464-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bd464-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd464-114">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bd464-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd464-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd464-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd464-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd464-116">See also</span></span>

- [<span data-ttu-id="bd464-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="bd464-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
