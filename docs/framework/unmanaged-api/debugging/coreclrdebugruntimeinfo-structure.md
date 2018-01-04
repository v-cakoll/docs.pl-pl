---
title: "CoreClrDebugRuntimeInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoreClrDebugRuntimeInfo
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: effcc44b3f3b0926c1d711955fa77aa3e71a1592
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="027b2-102">CoreClrDebugRuntimeInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="027b2-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="027b2-103">Reprezentuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) wystąpienia programu ładowany do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="027b2-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="027b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="027b2-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="027b2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="027b2-105">Members</span></span>  
  
|<span data-ttu-id="027b2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="027b2-106">Member</span></span>|<span data-ttu-id="027b2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="027b2-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="027b2-108">Identyfikator środowiska uruchomieniowego, który jest przypisany przez serwer proxy debugowania zdalnego uruchomiona na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="027b2-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="027b2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="027b2-109">Requirements</span></span>  
 <span data-ttu-id="027b2-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="027b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="027b2-111">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="027b2-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="027b2-112">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="027b2-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="027b2-113">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="027b2-113">**.NET Framework Versions:** 3.5 SP1</span></span>
