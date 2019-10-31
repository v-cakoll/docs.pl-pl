---
title: ICorDebugClass::GetModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: 94f2d20816bfc28118877f52c04237c41b3859e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125789"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="733ef-102">ICorDebugClass::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="733ef-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="733ef-103">Pobiera moduł, który definiuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="733ef-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="733ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="733ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="733ef-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="733ef-106">określoną Wskaźnik do adresu obiektu ICorDebugModule, który reprezentuje moduł, w którym jest zdefiniowana Ta klasa.</span><span class="sxs-lookup"><span data-stu-id="733ef-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="733ef-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="733ef-107">Requirements</span></span>  
 <span data-ttu-id="733ef-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="733ef-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="733ef-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="733ef-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="733ef-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="733ef-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="733ef-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733ef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
