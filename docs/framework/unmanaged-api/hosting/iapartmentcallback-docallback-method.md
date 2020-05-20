---
title: IApartmentCallback::DoCallback — Metoda
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 1a56c3ebe4b1c528f9c6555bdfbf1270a438410d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617116"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="738fa-102">IApartmentCallback::DoCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="738fa-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="738fa-103">Wykonuje określoną funkcję w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="738fa-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="738fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="738fa-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="738fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="738fa-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="738fa-106">podczas Wskaźnik do funkcji, która ma zostać wykonana w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="738fa-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="738fa-107">podczas Wskaźnik do argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="738fa-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="738fa-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="738fa-108">Requirements</span></span>  
 <span data-ttu-id="738fa-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="738fa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="738fa-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="738fa-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="738fa-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="738fa-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="738fa-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="738fa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738fa-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="738fa-113">See also</span></span>

- [<span data-ttu-id="738fa-114">IApartmentCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="738fa-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
