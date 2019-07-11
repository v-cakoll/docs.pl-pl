---
title: ICorDebugHandleValue::GetHandleType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0bc65cdeada059f6e9b41dc8eb4d7589a232143d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756824"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="561b7-102">ICorDebugHandleValue::GetHandleType — Metoda</span><span class="sxs-lookup"><span data-stu-id="561b7-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="561b7-103">Pobiera wartość wskazującą rodzaj uchwyt odwołuje się ten obiekt icordebughandlevalue —.</span><span class="sxs-lookup"><span data-stu-id="561b7-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="561b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="561b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="561b7-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="561b7-106">[out] Wskaźnik do wartości cordebughandletype — wyliczenie, który wskazuje na typ dojścia tego.</span><span class="sxs-lookup"><span data-stu-id="561b7-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="561b7-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="561b7-107">Requirements</span></span>  
 <span data-ttu-id="561b7-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561b7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561b7-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="561b7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="561b7-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="561b7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="561b7-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
