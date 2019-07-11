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
ms.openlocfilehash: b58832e110f67a54d3bd57a7284b2e26e43d6bf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739404"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="0deb5-102">CoreClrDebugRuntimeInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="0deb5-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="0deb5-103">Reprezentuje wystąpienie wspólnego środowiska uruchomieniowego (języka wspólnego CLR) języka, który jest załadowany do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="0deb5-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0deb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0deb5-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="0deb5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0deb5-105">Members</span></span>  
  
|<span data-ttu-id="0deb5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0deb5-106">Member</span></span>|<span data-ttu-id="0deb5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0deb5-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="0deb5-108">Identyfikator środowiska uruchomieniowego, który jest przypisany przez serwer proxy debugowania zdalnego uruchomioną na maszynie docelowej.</span><span class="sxs-lookup"><span data-stu-id="0deb5-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0deb5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0deb5-109">Requirements</span></span>  
 <span data-ttu-id="0deb5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0deb5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0deb5-111">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="0deb5-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0deb5-112">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0deb5-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0deb5-113">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="0deb5-113">**.NET Framework Versions:** 3.5 SP1</span></span>
