---
title: ICorPublishProcess::GetProcessID — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 728e8bdbce7f93176324d8f80261030f8cbae283
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140418"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="edc81-102">ICorPublishProcess::GetProcessID — Metoda</span><span class="sxs-lookup"><span data-stu-id="edc81-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="edc81-103">Pobiera identyfikator systemu operacyjnego dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="edc81-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edc81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edc81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edc81-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="edc81-106">określoną Wskaźnik do identyfikatora procesu reprezentowanego przez ten obiekt [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="edc81-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edc81-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edc81-107">Requirements</span></span>  
 <span data-ttu-id="edc81-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edc81-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edc81-109">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="edc81-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="edc81-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="edc81-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edc81-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edc81-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc81-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edc81-112">See also</span></span>

- [<span data-ttu-id="edc81-113">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="edc81-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
