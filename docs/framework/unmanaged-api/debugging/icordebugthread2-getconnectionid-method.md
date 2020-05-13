---
title: ICorDebugThread2::GetConnectionID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: c630daa50d465622c421381ac080eaa8d9d8d01d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379073"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="ae4b0-102">ICorDebugThread2::GetConnectionID — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae4b0-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="ae4b0-103">Pobiera identyfikator połączenia dla tego obiektu ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="ae4b0-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae4b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae4b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae4b0-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="ae4b0-106">określoną `CONNID`Reprezentuje identyfikator połączenia.</span><span class="sxs-lookup"><span data-stu-id="ae4b0-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae4b0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae4b0-107">Remarks</span></span>  
 <span data-ttu-id="ae4b0-108">`GetConnectionID`Metoda zwraca zero w `pdwConnectionId` parametrze, jeśli ten wątek nie jest częścią połączenia.</span><span class="sxs-lookup"><span data-stu-id="ae4b0-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="ae4b0-109">Jeśli ten wątek jest połączony z wystąpieniem Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` mapuje na identyfikator procesu serwera (SPID).</span><span class="sxs-lookup"><span data-stu-id="ae4b0-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae4b0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae4b0-110">Requirements</span></span>  
 <span data-ttu-id="ae4b0-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae4b0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae4b0-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae4b0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae4b0-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ae4b0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae4b0-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae4b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
