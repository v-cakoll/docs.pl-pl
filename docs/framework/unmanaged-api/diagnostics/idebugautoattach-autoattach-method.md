---
title: "IDebugAutoAttach::AutoAttach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b875fec2fdb6ecaeaccf8e58030b2fccbb8653b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="32673-102">IDebugAutoAttach::AutoAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="32673-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="32673-103">Wykonuje automatycznie wywoływane serwera debugera dołączyć.</span><span class="sxs-lookup"><span data-stu-id="32673-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32673-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32673-104">Syntax</span></span>  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32673-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32673-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="32673-106">[in] Zawsze ustawiony na wartość `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="32673-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="32673-107">[in] Identyfikator normalnie pobierane z procesu `GetCurrentProcessId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="32673-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="32673-108">[in] Program typu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, lub `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="32673-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="32673-109">[in] Identyfikator programu.</span><span class="sxs-lookup"><span data-stu-id="32673-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="32673-110">[in] Ciąg przekazany przez zlecenia debug.</span><span class="sxs-lookup"><span data-stu-id="32673-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32673-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32673-111">Return Value</span></span>  
 <span data-ttu-id="32673-112">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="32673-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32673-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32673-113">Requirements</span></span>  
 <span data-ttu-id="32673-114">**Nagłówek:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="32673-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32673-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32673-115">See Also</span></span>  
 [<span data-ttu-id="32673-116">IDebugAutoAttach, interfejs</span><span class="sxs-lookup"><span data-stu-id="32673-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
