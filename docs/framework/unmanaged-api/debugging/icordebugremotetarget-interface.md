---
title: "ICorDebugRemoteTarget — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38357072b3a6e8e8a326a16600b2d7ed56cdcb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="c2d67-102">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c2d67-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="c2d67-103">Udostępnia metody, które umożliwiają deweloperom debugowanie aplikacji Silverlight w wspólnego języka środowiska środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="c2d67-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2d67-104">Syntax</span></span>  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c2d67-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c2d67-105">Methods</span></span>  
  
|<span data-ttu-id="c2d67-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2d67-106">Method</span></span>|<span data-ttu-id="c2d67-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c2d67-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2d67-108">ICorDebugRemoteTarget::GetHostName — metoda</span><span class="sxs-lookup"><span data-stu-id="c2d67-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="c2d67-109">Zwraca nazwę hosta lub adres IP komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="c2d67-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d67-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2d67-110">Remarks</span></span>  
 <span data-ttu-id="c2d67-111">Debugowanie w trybie mieszanym (to znaczy kodu zarządzanego i natywnego) nie jest obsługiwana w systemie Windows 95, Windows 98 lub Windows ME ani na platformach innych niż x86 (na przykład IA-64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="c2d67-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d67-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2d67-112">Requirements</span></span>  
 <span data-ttu-id="c2d67-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d67-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d67-114">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c2d67-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c2d67-115">**Biblioteka:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d67-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d67-116">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="c2d67-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d67-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2d67-117">See Also</span></span>  
 [<span data-ttu-id="c2d67-118">ICorDebugRemote — interfejs</span><span class="sxs-lookup"><span data-stu-id="c2d67-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="c2d67-119">ICorDebug — interfejs</span><span class="sxs-lookup"><span data-stu-id="c2d67-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="c2d67-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="c2d67-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
