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
ms.openlocfilehash: 83cbfa097541681305ff285f21c2b6c9c6391ef8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703746"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="7c0dc-102">ICLRMetaHost::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c0dc-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="7c0dc-103">Próbuje bezpiecznie zamknąć wszystkie ładowane środowiska uruchomieniowe, a następnie kończy proces.</span><span class="sxs-lookup"><span data-stu-id="7c0dc-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="7c0dc-104">Zastępuje funkcję [CorExitProcess —](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7c0dc-104">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0dc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c0dc-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c0dc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c0dc-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="7c0dc-107">podczas Kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="7c0dc-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c0dc-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c0dc-108">Return Value</span></span>  
 <span data-ttu-id="7c0dc-109">Ta metoda nigdy nie zwraca, więc jej wartość zwracana jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="7c0dc-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c0dc-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c0dc-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c0dc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c0dc-111">Requirements</span></span>  
 <span data-ttu-id="7c0dc-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c0dc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c0dc-113">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="7c0dc-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7c0dc-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c0dc-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c0dc-115">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c0dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c0dc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c0dc-116">See also</span></span>

- [<span data-ttu-id="7c0dc-117">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c0dc-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="7c0dc-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="7c0dc-118">Hosting</span></span>](index.md)
