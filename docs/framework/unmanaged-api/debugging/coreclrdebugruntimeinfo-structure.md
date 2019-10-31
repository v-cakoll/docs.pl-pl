---
title: CoreClrDebugRuntimeInfo — Struktura
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
ms.openlocfilehash: 92a814d427fcf2e40c7f79e9eb9192e0b7eed4b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132140"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="65c77-102">CoreClrDebugRuntimeInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="65c77-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="65c77-103">Reprezentuje wystąpienie środowiska uruchomieniowego języka wspólnego (CLR), które jest ładowane w procesie na maszynie zdalnej.</span><span class="sxs-lookup"><span data-stu-id="65c77-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65c77-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="65c77-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="65c77-105">Members</span></span>  
  
|<span data-ttu-id="65c77-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="65c77-106">Member</span></span>|<span data-ttu-id="65c77-107">Opis</span><span class="sxs-lookup"><span data-stu-id="65c77-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="65c77-108">Identyfikator środowiska uruchomieniowego, który jest przypisany przez zdalny serwer proxy uruchomiony na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="65c77-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65c77-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65c77-109">Requirements</span></span>  
 <span data-ttu-id="65c77-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c77-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c77-111">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="65c77-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="65c77-112">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="65c77-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="65c77-113">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="65c77-113">**.NET Framework Versions:** 3.5 SP1</span></span>
