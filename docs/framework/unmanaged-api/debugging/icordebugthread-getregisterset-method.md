---
title: "ICorDebugThread::GetRegisterSet — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9add4dd94669bf41e65793249d05f85700b18cb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="999c1-102">ICorDebugThread::GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="999c1-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="999c1-103">Pobiera wskaźnika interfejsu do zestawu rejestru, który jest skojarzony z active częścią tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="999c1-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="999c1-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="999c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="999c1-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="999c1-106">[out] Wskaźnik do adresu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) obiekt interfejsu, który reprezentuje rejestru ustawić active części tego wątku.</span><span class="sxs-lookup"><span data-stu-id="999c1-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999c1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="999c1-107">Requirements</span></span>  
 <span data-ttu-id="999c1-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="999c1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="999c1-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="999c1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="999c1-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="999c1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="999c1-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="999c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
