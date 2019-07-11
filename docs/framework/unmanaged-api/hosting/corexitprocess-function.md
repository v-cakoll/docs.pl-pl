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
ms.openlocfilehash: 7aaa0e83de1b1c3e2ce436de04a36addef16c057
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758518"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="7f1df-102">CorExitProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7f1df-102">CorExitProcess Function</span></span>
<span data-ttu-id="7f1df-103">Zamyka bieżący proces niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="7f1df-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="7f1df-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7f1df-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="7f1df-105">Użyj [iclrmetahost::exitprocess —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="7f1df-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1df-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f1df-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f1df-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f1df-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="7f1df-108">Liczba całkowita, która określa kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="7f1df-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f1df-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f1df-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f1df-110">Począwszy od programu .NET Framework 4, `CorExitProcess` kończy działanie każdej wprowadzenie środowiska uruchomieniowego w procesie, a nie tylko środowiska uruchomieniowego, powiązana starszych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="7f1df-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1df-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f1df-111">Requirements</span></span>  
 <span data-ttu-id="7f1df-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1df-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f1df-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f1df-114">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f1df-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f1df-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1df-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f1df-116">See also</span></span>

- [<span data-ttu-id="7f1df-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="7f1df-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
