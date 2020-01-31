---
title: ICorDebugRemoteTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: bab6b7f683b5563cf362366dfb007f83caeee12d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791939"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="edfc8-102">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="edfc8-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="edfc8-103">Dostarcza metody, które umożliwiają deweloperom debugowanie aplikacji opartych na technologii Silverlight w środowisku środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="edfc8-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edfc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edfc8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="edfc8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="edfc8-105">Methods</span></span>  
  
|<span data-ttu-id="edfc8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="edfc8-106">Method</span></span>|<span data-ttu-id="edfc8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="edfc8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="edfc8-108">ICorDebugRemoteTarget::GetHostName, metoda</span><span class="sxs-lookup"><span data-stu-id="edfc8-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="edfc8-109">Zwraca nazwę hosta lub adres IP komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="edfc8-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edfc8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edfc8-110">Remarks</span></span>  
 <span data-ttu-id="edfc8-111">Debugowanie w trybie mieszanym (czyli kod zarządzany i natywny) nie jest obsługiwane w systemach Windows 95, Windows 98 lub Windows ME ani na platformach innych niż x86 (takich jak IA-64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="edfc8-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edfc8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edfc8-112">Requirements</span></span>  
 <span data-ttu-id="edfc8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edfc8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edfc8-114">**Nagłówek:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="edfc8-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="edfc8-115">**Library:** : CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="edfc8-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="edfc8-116">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="edfc8-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edfc8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edfc8-117">See also</span></span>

- [<span data-ttu-id="edfc8-118">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="edfc8-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="edfc8-119">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="edfc8-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="edfc8-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="edfc8-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
