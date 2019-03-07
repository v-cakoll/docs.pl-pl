---
title: IBindingDisplay::InitializeForProcess — Metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aabad159b521207fed976636ae8b9e338f09ac42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466184"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="64aae-102">IBindingDisplay::InitializeForProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="64aae-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="64aae-103">Inicjuje [ibindingdisplay —](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="64aae-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64aae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64aae-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64aae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64aae-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="64aae-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="64aae-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64aae-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64aae-107">Remarks</span></span>  
 <span data-ttu-id="64aae-108">Wywołuje debugera `InitializeForProcess` metody w czasie tworzenia zainicjować wyświetlania powiązania.</span><span class="sxs-lookup"><span data-stu-id="64aae-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="64aae-109">`InitializeForProcess` musi zostać wywołana w czasie tworzenia przed innej metody w `IBindingDisplay` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="64aae-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64aae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64aae-110">Requirements</span></span>  
 <span data-ttu-id="64aae-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64aae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64aae-112">**Nagłówek:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="64aae-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="64aae-113">**Biblioteka:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="64aae-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="64aae-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64aae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64aae-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64aae-115">See also</span></span>
- [<span data-ttu-id="64aae-116">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="64aae-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
