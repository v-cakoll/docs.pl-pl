---
title: ICoreClrDebugTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: c44a12ef377d29e0b33b8be86aa1d8f0aa9d26bd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397153"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="6c889-102">ICoreClrDebugTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6c889-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="6c889-103">Zapewnia metody, które kontrolują liczby odwołań, wyliczają procesy i zwalniają pamięć skojarzoną z debugerem, który jest dołączony do zdalnego obiektu docelowego Silverlight platformy Macintosh.</span><span class="sxs-lookup"><span data-stu-id="6c889-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c889-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c889-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6c889-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6c889-105">Methods</span></span>  
  
|<span data-ttu-id="6c889-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6c889-106">Method</span></span>|<span data-ttu-id="6c889-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6c889-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c889-108">ICoreClrDebugTarget::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c889-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="6c889-109">Wylicza procesy, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="6c889-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="6c889-110">ICoreClrDebugTarget::EnumRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c889-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="6c889-111">Wylicza środowisko uruchomieniowe języka wspólnego (CLRs) w określonym procesie na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="6c889-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="6c889-112">ICoreClrDebugTarget::FreeMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c889-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="6c889-113">Zwalnia pamięć przydzieloną przez metody wyliczenia w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="6c889-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c889-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c889-114">Remarks</span></span>  
 <span data-ttu-id="6c889-115">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania obiektu docelowego aplikacji opartego na technologii Silverlight, który jest uruchomiony na komputerze zdalnym Macintosh.</span><span class="sxs-lookup"><span data-stu-id="6c889-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c889-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c889-116">Requirements</span></span>  
 <span data-ttu-id="6c889-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c889-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c889-118">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="6c889-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="6c889-119">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="6c889-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="6c889-120">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="6c889-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c889-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c889-121">See also</span></span>

- [<span data-ttu-id="6c889-122">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6c889-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="6c889-123">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6c889-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="6c889-124">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6c889-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
