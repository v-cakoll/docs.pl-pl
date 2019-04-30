---
title: ICorDebugModule::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540288f83de9c3c6ff2111330c77ded48abd6d5f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761666"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="4b36e-102">ICorDebugModule::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b36e-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="4b36e-103">Pobiera rozmiar w bajtach modułu.</span><span class="sxs-lookup"><span data-stu-id="4b36e-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b36e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b36e-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b36e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b36e-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="4b36e-106">[out] Rozmiar modułu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="4b36e-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="4b36e-107">Moduł został utworzony z generatorem obrazu natywnego (NGen.exe), rozmiar modułu będzie mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="4b36e-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b36e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b36e-108">Requirements</span></span>  
 <span data-ttu-id="4b36e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b36e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b36e-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b36e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b36e-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b36e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b36e-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b36e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
