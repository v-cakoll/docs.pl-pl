---
title: ICLRMetaHost::ExitProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc71762fb4a660cf84814cdd46d09696a161f3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431600"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="e2369-102">ICLRMetaHost::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2369-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="e2369-103">Podejmuje próbę prawidłowe zamknięcie wszystkich załadowanych środowisk uruchomieniowych, a następnie kończy proces.</span><span class="sxs-lookup"><span data-stu-id="e2369-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="e2369-104">Zastępuje [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="e2369-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2369-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2369-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2369-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2369-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="e2369-107">[in] Kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="e2369-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2369-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e2369-108">Return Value</span></span>  
 <span data-ttu-id="e2369-109">Ta metoda nigdy nie powraca, więc jego zwracanych wartości są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e2369-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2369-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2369-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2369-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2369-111">Requirements</span></span>  
 <span data-ttu-id="e2369-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2369-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2369-113">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e2369-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e2369-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2369-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2369-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2369-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2369-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2369-116">See Also</span></span>  
 [<span data-ttu-id="e2369-117">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2369-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="e2369-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="e2369-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
