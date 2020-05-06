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
ms.openlocfilehash: 2c41e7db32ee8557a6c03217b95fd5b040655c70
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860928"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="7a1b1-102">CoreClrDebugRuntimeInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="7a1b1-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="7a1b1-103">Reprezentuje wystąpienie środowiska uruchomieniowego języka wspólnego (CLR), które jest ładowane w procesie na maszynie zdalnej.</span><span class="sxs-lookup"><span data-stu-id="7a1b1-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a1b1-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7a1b1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7a1b1-105">Members</span></span>  
  
|<span data-ttu-id="7a1b1-106">Członek</span><span class="sxs-lookup"><span data-stu-id="7a1b1-106">Member</span></span>|<span data-ttu-id="7a1b1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7a1b1-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="7a1b1-108">Identyfikator środowiska uruchomieniowego, który jest przypisany przez zdalny serwer proxy uruchomiony na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="7a1b1-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a1b1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a1b1-109">Requirements</span></span>  
 <span data-ttu-id="7a1b1-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a1b1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1b1-111">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="7a1b1-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7a1b1-112">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="7a1b1-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7a1b1-113">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7a1b1-113">**.NET Framework Versions:** 3.5 SP1</span></span>
