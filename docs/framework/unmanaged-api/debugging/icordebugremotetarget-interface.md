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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae31506d4ba34bf262f49bc2321c6cfcd30f1b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782697"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="bf4a1-102">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf4a1-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="bf4a1-103">Udostępnia metody, które umożliwiają deweloperom debugowania aplikacji opartych na technologii Silverlight w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="bf4a1-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf4a1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="bf4a1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bf4a1-105">Methods</span></span>  
  
|<span data-ttu-id="bf4a1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf4a1-106">Method</span></span>|<span data-ttu-id="bf4a1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf4a1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf4a1-108">ICorDebugRemoteTarget::GetHostName, metoda</span><span class="sxs-lookup"><span data-stu-id="bf4a1-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="bf4a1-109">Zwraca nazwę hosta lub adres IP komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="bf4a1-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf4a1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf4a1-110">Remarks</span></span>  
 <span data-ttu-id="bf4a1-111">Debugowanie trybu mieszanego (czyli kodu zarządzanego i natywnego) nie jest obsługiwana na Windows 95, Windows 98 lub Windows ME lub na platformach innych niż x86 (takich jak IA-64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="bf4a1-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf4a1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf4a1-112">Requirements</span></span>  
 <span data-ttu-id="bf4a1-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf4a1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf4a1-114">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="bf4a1-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="bf4a1-115">**Biblioteka:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf4a1-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf4a1-116">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="bf4a1-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4a1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf4a1-117">See also</span></span>

- [<span data-ttu-id="bf4a1-118">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf4a1-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="bf4a1-119">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf4a1-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="bf4a1-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bf4a1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
