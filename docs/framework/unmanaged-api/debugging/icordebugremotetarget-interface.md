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
ms.openlocfilehash: 4883c208468db0096bed3ff8cf4a8ed50a5d7cc6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379232"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="1e552-102">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1e552-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="1e552-103">Dostarcza metody, które umożliwiają deweloperom debugowanie aplikacji opartych na technologii Silverlight w środowisku środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1e552-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e552-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e552-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1e552-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1e552-105">Methods</span></span>  
  
|<span data-ttu-id="1e552-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e552-106">Method</span></span>|<span data-ttu-id="1e552-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1e552-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e552-108">ICorDebugRemoteTarget::GetHostName — Metoda</span><span class="sxs-lookup"><span data-stu-id="1e552-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="1e552-109">Zwraca nazwę hosta lub adres IP komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="1e552-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e552-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e552-110">Remarks</span></span>  
 <span data-ttu-id="1e552-111">Debugowanie w trybie mieszanym (czyli kod zarządzany i natywny) nie jest obsługiwane w systemach Windows 95, Windows 98 lub Windows ME ani na platformach innych niż x86 (takich jak IA-64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="1e552-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e552-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1e552-112">Requirements</span></span>  
 <span data-ttu-id="1e552-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e552-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e552-114">**Nagłówek:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="1e552-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1e552-115">**Library:** : CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1e552-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e552-116">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="1e552-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e552-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e552-117">See also</span></span>

- [<span data-ttu-id="1e552-118">ICorDebugRemote — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1e552-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="1e552-119">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1e552-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="1e552-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1e552-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
