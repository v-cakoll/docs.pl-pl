---
title: ICorPublish::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 0368349e6c6a566cb569738bf3bda40eb9f5de96
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790733"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="c2949-102">ICorPublish::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2949-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="c2949-103">Pobiera wystąpienie [ICorPublishProcess](icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="c2949-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2949-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2949-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2949-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2949-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="c2949-106">podczas Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="c2949-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c2949-107">określoną Wskaźnik do adresu `ICorPublishProcess` wystąpienia, które reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="c2949-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2949-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2949-108">Remarks</span></span>  
 <span data-ttu-id="c2949-109">`GetProcess`, jeśli proces nie istnieje lub nie jest procesem zarządzanym, który może być debugowany przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c2949-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2949-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2949-110">Requirements</span></span>  
 <span data-ttu-id="c2949-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2949-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2949-112">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c2949-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c2949-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2949-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2949-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2949-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2949-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2949-115">See also</span></span>

- [<span data-ttu-id="c2949-116">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2949-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
