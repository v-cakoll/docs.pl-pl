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
ms.openlocfilehash: b9d4b27ca0bf454b42f15b849008e5a3019bb09a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864081"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="25e8d-102">CoreClrDebugProcInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="25e8d-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="25e8d-103">Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="25e8d-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25e8d-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="25e8d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="25e8d-105">Members</span></span>  
  
|<span data-ttu-id="25e8d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="25e8d-106">Member</span></span>|<span data-ttu-id="25e8d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="25e8d-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="25e8d-108">Identyfikator procesu przypisaną przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="25e8d-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="25e8d-109">Identyfikator procesu, który jest przypisany przez serwer proxy debugowania zdalnego uruchomioną na maszynie docelowej.</span><span class="sxs-lookup"><span data-stu-id="25e8d-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="25e8d-110">Ten identyfikator jest odtwarzana częściej niż identyfikator systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="25e8d-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="25e8d-111">Wiersza polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="25e8d-111">Command-line of the process.</span></span> <span data-ttu-id="25e8d-112">Ten element członkowski może zostać obcięty.</span><span class="sxs-lookup"><span data-stu-id="25e8d-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25e8d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25e8d-113">Requirements</span></span>  
 <span data-ttu-id="25e8d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25e8d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25e8d-115">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="25e8d-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="25e8d-116">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="25e8d-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="25e8d-117">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="25e8d-117">**.NET Framework Versions:** 3.5 SP1</span></span>
