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
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442127"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="03556-102">IDebugAutoAttach::AutoAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="03556-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="03556-103">Wykonuje automatyczne dołączanie debugera wywoływanego przez serwer.</span><span class="sxs-lookup"><span data-stu-id="03556-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03556-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03556-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="03556-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03556-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="03556-106">podczas Zawsze ustawiaj na `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="03556-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="03556-107">podczas Identyfikator procesu, zwykle pobierany z `GetCurrentProcessId` funkcją.</span><span class="sxs-lookup"><span data-stu-id="03556-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="03556-108">podczas Typ programu: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , lub `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="03556-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="03556-109">podczas Identyfikator programu.</span><span class="sxs-lookup"><span data-stu-id="03556-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="03556-110">podczas Ciąg przesłany przez czasownik debugowania.</span><span class="sxs-lookup"><span data-stu-id="03556-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03556-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03556-111">Return Value</span></span>  
 <span data-ttu-id="03556-112">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="03556-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03556-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03556-113">Requirements</span></span>  
 <span data-ttu-id="03556-114">**Nagłówek:** DbgAutoAttach. h</span><span class="sxs-lookup"><span data-stu-id="03556-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03556-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03556-115">See also</span></span>

- [<span data-ttu-id="03556-116">IDebugAutoAttach — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03556-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
