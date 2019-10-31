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
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138692"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="3ea4e-102">ICorDebugThread2::GetConnectionID — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ea4e-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="3ea4e-103">Pobiera identyfikator połączenia dla tego obiektu ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ea4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ea4e-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="3ea4e-106">określoną `CONNID`, który reprezentuje identyfikator połączenia.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ea4e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ea4e-107">Remarks</span></span>  
 <span data-ttu-id="3ea4e-108">Metoda `GetConnectionID` zwraca zero w parametrze `pdwConnectionId`, jeśli ten wątek nie jest częścią połączenia.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="3ea4e-109">Jeśli ten wątek jest połączony z wystąpieniem programu Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` jest mapowany na identyfikator procesu serwera (SPID).</span><span class="sxs-lookup"><span data-stu-id="3ea4e-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea4e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ea4e-110">Requirements</span></span>  
 <span data-ttu-id="3ea4e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea4e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea4e-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ea4e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ea4e-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ea4e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ea4e-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea4e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
