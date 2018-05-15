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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="dbb69-102">CoreClrDebugProcInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="dbb69-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="dbb69-103">Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="dbb69-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbb69-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="dbb69-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dbb69-105">Members</span></span>  
  
|<span data-ttu-id="dbb69-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dbb69-106">Member</span></span>|<span data-ttu-id="dbb69-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dbb69-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="dbb69-108">Identyfikator procesu przypisane systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dbb69-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="dbb69-109">Identyfikator procesu, który jest przypisany przez serwer proxy debugowania zdalnego uruchomiona na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="dbb69-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="dbb69-110">Ten identyfikator jest odtwarzana częściej niż identyfikator systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dbb69-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="dbb69-111">Wiersza polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="dbb69-111">Command-line of the process.</span></span> <span data-ttu-id="dbb69-112">Ten element członkowski może zostać obcięty.</span><span class="sxs-lookup"><span data-stu-id="dbb69-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbb69-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbb69-113">Requirements</span></span>  
 <span data-ttu-id="dbb69-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbb69-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb69-115">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="dbb69-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="dbb69-116">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="dbb69-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="dbb69-117">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="dbb69-117">**.NET Framework Versions:** 3.5 SP1</span></span>
