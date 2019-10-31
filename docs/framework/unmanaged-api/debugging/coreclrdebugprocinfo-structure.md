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
ms.openlocfilehash: e12882e53d1aa2120ab5c4b6793d7f2e34be76eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132164"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="5a452-102">CoreClrDebugProcInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="5a452-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="5a452-103">Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="5a452-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a452-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a452-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="5a452-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5a452-105">Members</span></span>  
  
|<span data-ttu-id="5a452-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5a452-106">Member</span></span>|<span data-ttu-id="5a452-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5a452-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="5a452-108">Identyfikator procesu przypisany do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5a452-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="5a452-109">Identyfikator procesu, który jest przypisywany przez zdalny serwer proxy na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="5a452-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="5a452-110">Ten identyfikator jest odtwarzany rzadziej niż identyfikator systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5a452-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="5a452-111">Wiersz polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="5a452-111">Command-line of the process.</span></span> <span data-ttu-id="5a452-112">Ten element członkowski może zostać obcięty.</span><span class="sxs-lookup"><span data-stu-id="5a452-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a452-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a452-113">Requirements</span></span>  
 <span data-ttu-id="5a452-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a452-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a452-115">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="5a452-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5a452-116">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="5a452-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5a452-117">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="5a452-117">**.NET Framework Versions:** 3.5 SP1</span></span>
