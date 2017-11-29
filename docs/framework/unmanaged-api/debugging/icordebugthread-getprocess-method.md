---
title: "ICorDebugThread::GetProcess — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be58714856b93a244248fb97d6cc1e1b4ec476c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="bb407-102">ICorDebugThread::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb407-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="bb407-103">Pobiera wskaźnika interfejsu, do której część stanowi ICorDebugThread tego procesu.</span><span class="sxs-lookup"><span data-stu-id="bb407-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb407-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb407-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb407-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb407-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="bb407-106">[out] Wskaźnik do adresu ICorDebugProcess obiektu interfejsu, który reprezentuje procesu.</span><span class="sxs-lookup"><span data-stu-id="bb407-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb407-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb407-107">Requirements</span></span>  
 <span data-ttu-id="bb407-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb407-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb407-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb407-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb407-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb407-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb407-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb407-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
