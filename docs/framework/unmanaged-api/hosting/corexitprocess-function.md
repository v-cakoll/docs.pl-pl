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
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176464"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="47ed3-102">CorExitProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="47ed3-102">CorExitProcess Function</span></span>
<span data-ttu-id="47ed3-103">Zamyka bieżący proces niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="47ed3-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="47ed3-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="47ed3-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="47ed3-105">Zamiast tego należy użyć metody [ICLRMetaHost::ExitProcess.](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)</span><span class="sxs-lookup"><span data-stu-id="47ed3-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ed3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="47ed3-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47ed3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="47ed3-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="47ed3-108">Liczba całkowita określająca kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="47ed3-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47ed3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47ed3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47ed3-110">Począwszy od programu .NET `CorExitProcess` Framework 4, kończy każde uruchomione środowisko uruchomieniowe w procesie, a nie tylko środowisko uruchomieniowe, do którego zostały powiązane starsze interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="47ed3-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ed3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47ed3-111">Requirements</span></span>  
 <span data-ttu-id="47ed3-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ed3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ed3-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47ed3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47ed3-114">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="47ed3-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47ed3-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ed3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ed3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47ed3-116">See also</span></span>

- [<span data-ttu-id="47ed3-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="47ed3-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
