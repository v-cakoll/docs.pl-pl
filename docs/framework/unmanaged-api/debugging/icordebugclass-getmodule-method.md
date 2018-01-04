---
title: "ICorDebugClass::GetModule — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77997d083a184ff20df749933f21eefafc2b9e3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="a2e13-102">ICorDebugClass::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2e13-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="a2e13-103">Pobiera moduł, który definiuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="a2e13-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2e13-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2e13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2e13-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="a2e13-106">[out] Wskaźnik do adresu ICorDebugModule obiekt, który reprezentuje modułu, w którym ta klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="a2e13-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e13-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2e13-107">Requirements</span></span>  
 <span data-ttu-id="a2e13-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e13-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e13-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2e13-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2e13-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2e13-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2e13-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e13-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
