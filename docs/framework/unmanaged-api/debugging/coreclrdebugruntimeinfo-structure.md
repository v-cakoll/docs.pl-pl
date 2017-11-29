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
ms.openlocfilehash: 0e18416822aed6020fb0de8eb5bc7d38e4cd2eb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="9f73f-102">CoreClrDebugRuntimeInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="9f73f-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="9f73f-103">Reprezentuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) wystąpienia programu ładowany do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="9f73f-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f73f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f73f-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="9f73f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9f73f-105">Members</span></span>  
  
|<span data-ttu-id="9f73f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9f73f-106">Member</span></span>|<span data-ttu-id="9f73f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9f73f-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="9f73f-108">Identyfikator środowiska uruchomieniowego, który jest przypisany przez serwer proxy debugowania zdalnego uruchomiona na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="9f73f-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f73f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f73f-109">Requirements</span></span>  
 <span data-ttu-id="9f73f-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f73f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f73f-111">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="9f73f-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="9f73f-112">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="9f73f-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="9f73f-113">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="9f73f-113">**.NET Framework Versions:** 3.5 SP1</span></span>
