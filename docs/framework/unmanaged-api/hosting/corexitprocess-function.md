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
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616570"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="b325c-102">CorExitProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b325c-102">CorExitProcess Function</span></span>
<span data-ttu-id="b325c-103">Zamyka bieżący proces niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="b325c-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="b325c-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b325c-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="b325c-105">Zamiast tego użyj metody [ICLRMetaHost:: ExitProcess —](iclrmetahost-exitprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b325c-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b325c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b325c-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b325c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b325c-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="b325c-108">Liczba całkowita, która określa kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="b325c-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b325c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b325c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b325c-110">Począwszy od .NET Framework 4, `CorExitProcess` zamyka wszystkie uruchomione środowisko uruchomieniowe w procesie, a nie tylko środowisko uruchomieniowe, do którego zostały powiązane starsze interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="b325c-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b325c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b325c-111">Requirements</span></span>  
 <span data-ttu-id="b325c-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b325c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b325c-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b325c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b325c-114">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b325c-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b325c-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b325c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b325c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b325c-116">See also</span></span>

- [<span data-ttu-id="b325c-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b325c-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
