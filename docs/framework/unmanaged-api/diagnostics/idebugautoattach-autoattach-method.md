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
ms.openlocfilehash: 766aeb31436101babeab31b615a1c633578bfcc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445524"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="0b92f-102">IDebugAutoAttach::AutoAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b92f-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="0b92f-103">Wykonuje automatyczne dołączanie debugera wywoływanego przez serwer.</span><span class="sxs-lookup"><span data-stu-id="0b92f-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b92f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b92f-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b92f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b92f-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="0b92f-106">podczas Zawsze ustawiaj na `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="0b92f-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="0b92f-107">podczas Identyfikator procesu, zwykle pobierany z funkcją `GetCurrentProcessId`.</span><span class="sxs-lookup"><span data-stu-id="0b92f-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="0b92f-108">podczas Typ programu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`lub `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="0b92f-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="0b92f-109">podczas Identyfikator programu.</span><span class="sxs-lookup"><span data-stu-id="0b92f-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="0b92f-110">podczas Ciąg przesłany przez czasownik debugowania.</span><span class="sxs-lookup"><span data-stu-id="0b92f-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b92f-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="0b92f-111">Return Value</span></span>  
 <span data-ttu-id="0b92f-112">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b92f-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b92f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b92f-113">Requirements</span></span>  
 <span data-ttu-id="0b92f-114">**Nagłówek:** DbgAutoAttach. h</span><span class="sxs-lookup"><span data-stu-id="0b92f-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b92f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b92f-115">See also</span></span>

- [<span data-ttu-id="0b92f-116">IDebugAutoAttach, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b92f-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
