---
title: CoreClrDebugProcInfo — Struktura
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fc34add4038d25d60e4728847e0d84914a14e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739416"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="7b43c-102">CoreClrDebugProcInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="7b43c-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="7b43c-103">Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7b43c-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b43c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b43c-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7b43c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7b43c-105">Members</span></span>  
  
|<span data-ttu-id="7b43c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7b43c-106">Member</span></span>|<span data-ttu-id="7b43c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7b43c-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="7b43c-108">Identyfikator procesu przypisaną przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="7b43c-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="7b43c-109">Identyfikator procesu, który jest przypisany przez serwer proxy debugowania zdalnego uruchomioną na maszynie docelowej.</span><span class="sxs-lookup"><span data-stu-id="7b43c-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="7b43c-110">Ten identyfikator jest odtwarzana częściej niż identyfikator systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7b43c-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="7b43c-111">Wiersza polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="7b43c-111">Command-line of the process.</span></span> <span data-ttu-id="7b43c-112">Ten element członkowski może zostać obcięty.</span><span class="sxs-lookup"><span data-stu-id="7b43c-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b43c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b43c-113">Requirements</span></span>  
 <span data-ttu-id="7b43c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b43c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b43c-115">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="7b43c-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7b43c-116">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7b43c-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7b43c-117">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="7b43c-117">**.NET Framework Versions:** 3.5 SP1</span></span>
