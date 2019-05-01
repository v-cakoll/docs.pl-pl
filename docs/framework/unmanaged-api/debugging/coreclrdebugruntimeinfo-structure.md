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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88fcc5959054f1cdf7c9543674584a4bde26d896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966045"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="07089-102">CoreClrDebugRuntimeInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="07089-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="07089-103">Reprezentuje wystąpienie wspólnego środowiska uruchomieniowego (języka wspólnego CLR) języka, który jest załadowany do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="07089-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07089-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07089-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="07089-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="07089-105">Members</span></span>  
  
|<span data-ttu-id="07089-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="07089-106">Member</span></span>|<span data-ttu-id="07089-107">Opis</span><span class="sxs-lookup"><span data-stu-id="07089-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="07089-108">Identyfikator środowiska uruchomieniowego, który jest przypisany przez serwer proxy debugowania zdalnego uruchomioną na maszynie docelowej.</span><span class="sxs-lookup"><span data-stu-id="07089-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07089-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07089-109">Requirements</span></span>  
 <span data-ttu-id="07089-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07089-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07089-111">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="07089-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="07089-112">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="07089-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="07089-113">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="07089-113">**.NET Framework Versions:** 3.5 SP1</span></span>
