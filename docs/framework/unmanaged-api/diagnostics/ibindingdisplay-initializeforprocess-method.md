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
ms.openlocfilehash: 8954c2f6ecaf2767dd01b0601096d9e3f6df9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="8b8dc-102">IBindingDisplay::InitializeForProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b8dc-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="8b8dc-103">Inicjuje [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b8dc-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b8dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b8dc-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b8dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b8dc-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="8b8dc-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="8b8dc-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b8dc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b8dc-107">Remarks</span></span>  
 <span data-ttu-id="8b8dc-108">Wywołań debugera `InitializeForProcess` metody w czasie tworzenia, aby zainicjować ekran powiązania.</span><span class="sxs-lookup"><span data-stu-id="8b8dc-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="8b8dc-109">`InitializeForProcess` musi zostać wywołana w czasie tworzenia przed innej metody w `IBindingDisplay` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8b8dc-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b8dc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b8dc-110">Requirements</span></span>  
 <span data-ttu-id="8b8dc-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b8dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b8dc-112">**Nagłówek:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="8b8dc-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="8b8dc-113">**Biblioteka:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="8b8dc-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="8b8dc-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b8dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8dc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b8dc-115">See Also</span></span>  
 [<span data-ttu-id="8b8dc-116">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b8dc-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
