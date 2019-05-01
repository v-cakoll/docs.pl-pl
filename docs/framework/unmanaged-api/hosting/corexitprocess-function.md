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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95625cfe17b36c0244e6780a08dcf50ce50763d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985819"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="cd7a5-102">CorExitProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="cd7a5-102">CorExitProcess Function</span></span>
<span data-ttu-id="cd7a5-103">Zamyka bieżący proces niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="cd7a5-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="cd7a5-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd7a5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="cd7a5-105">Użyj [iclrmetahost::exitprocess —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cd7a5-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7a5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd7a5-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd7a5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd7a5-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="cd7a5-108">Liczba całkowita, która określa kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="cd7a5-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd7a5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd7a5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd7a5-110">Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` kończy działanie każdej wprowadzenie środowiska uruchomieniowego w procesie, a nie tylko środowiska uruchomieniowego, powiązana starszych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="cd7a5-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd7a5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd7a5-111">Requirements</span></span>  
 <span data-ttu-id="cd7a5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd7a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7a5-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd7a5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd7a5-114">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd7a5-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd7a5-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd7a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7a5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd7a5-116">See also</span></span>

- [<span data-ttu-id="cd7a5-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="cd7a5-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
