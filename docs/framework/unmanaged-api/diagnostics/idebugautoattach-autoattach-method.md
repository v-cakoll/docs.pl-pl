---
title: IDebugAutoAttach::AutoAttach — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16ccc56579a1ebe45ada61a9565cc8ade335333d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469681"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="01906-102">IDebugAutoAttach::AutoAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="01906-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="01906-103">Wykonuje automatyczne wywoływane serwer debugera dołączania.</span><span class="sxs-lookup"><span data-stu-id="01906-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01906-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01906-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="01906-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01906-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="01906-106">[in] Zawsze ustawiony na wartość `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="01906-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="01906-107">[in] Identyfikator, zwykle pobierane za pomocą procesu `GetCurrentProcessId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="01906-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="01906-108">[in] Typ programu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, lub `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="01906-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="01906-109">[in] Identyfikator programu.</span><span class="sxs-lookup"><span data-stu-id="01906-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="01906-110">[in] Ciąg przekazywany przez czasownik debug.</span><span class="sxs-lookup"><span data-stu-id="01906-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01906-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="01906-111">Return Value</span></span>  
 <span data-ttu-id="01906-112">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="01906-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01906-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01906-113">Requirements</span></span>  
 <span data-ttu-id="01906-114">**Nagłówek:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="01906-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01906-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01906-115">See also</span></span>
- [<span data-ttu-id="01906-116">IDebugAutoAttach, interfejs</span><span class="sxs-lookup"><span data-stu-id="01906-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
