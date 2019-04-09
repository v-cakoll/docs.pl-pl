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
ms.openlocfilehash: 5064e66708044d82e3a097c8235b5b28a3412200
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077137"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="ad069-102">IDebugAutoAttach::AutoAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad069-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="ad069-103">Wykonuje automatyczne wywoływane serwer debugera dołączania.</span><span class="sxs-lookup"><span data-stu-id="ad069-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad069-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad069-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ad069-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad069-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="ad069-106">[in] Zawsze ustawiony na wartość `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="ad069-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="ad069-107">[in] Identyfikator, zwykle pobierane za pomocą procesu `GetCurrentProcessId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="ad069-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="ad069-108">[in] Typ programu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, lub `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="ad069-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="ad069-109">[in] Identyfikator programu.</span><span class="sxs-lookup"><span data-stu-id="ad069-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="ad069-110">[in] Ciąg przekazywany przez czasownik debug.</span><span class="sxs-lookup"><span data-stu-id="ad069-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad069-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ad069-111">Return Value</span></span>  
 <span data-ttu-id="ad069-112">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ad069-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad069-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad069-113">Requirements</span></span>  
 <span data-ttu-id="ad069-114">**Nagłówek:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="ad069-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad069-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad069-115">See also</span></span>

- [<span data-ttu-id="ad069-116">IDebugAutoAttach — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ad069-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
