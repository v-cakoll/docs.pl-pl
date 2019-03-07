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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d51e21eab4ac1edc81b58171e5382ada170a57f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468952"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="f91f5-102">ICorDebugThread2::GetConnectionID — Metoda</span><span class="sxs-lookup"><span data-stu-id="f91f5-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="f91f5-103">Pobiera identyfikator połączenia dla tego obiektu icordebugthread2 —.</span><span class="sxs-lookup"><span data-stu-id="f91f5-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f91f5-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f91f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f91f5-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="f91f5-106">[out] A `CONNID` reprezentujący identyfikator połączenia.</span><span class="sxs-lookup"><span data-stu-id="f91f5-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f91f5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f91f5-107">Remarks</span></span>  
 <span data-ttu-id="f91f5-108">`GetConnectionID` Metoda zwraca zero w `pdwConnectionId` parametru, jeśli ten wątek nie jest częścią połączenia.</span><span class="sxs-lookup"><span data-stu-id="f91f5-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="f91f5-109">Jeśli ten wątek jest podłączony do wystąpienia programu Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` mapuje do identyfikatora procesu serwera (SPID).</span><span class="sxs-lookup"><span data-stu-id="f91f5-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91f5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f91f5-110">Requirements</span></span>  
 <span data-ttu-id="f91f5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f91f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f91f5-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f91f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f91f5-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f91f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f91f5-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f91f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
