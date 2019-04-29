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
ms.openlocfilehash: aa1e85751f90c34d40e88207af5c7eed2dd1bb82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599367"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="ce16b-102">IBindingDisplay::InitializeForProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce16b-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="ce16b-103">Inicjuje [ibindingdisplay —](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="ce16b-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce16b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce16b-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce16b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce16b-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="ce16b-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="ce16b-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce16b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce16b-107">Remarks</span></span>  
 <span data-ttu-id="ce16b-108">Wywołuje debugera `InitializeForProcess` metody w czasie tworzenia zainicjować wyświetlania powiązania.</span><span class="sxs-lookup"><span data-stu-id="ce16b-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="ce16b-109">`InitializeForProcess` musi zostać wywołana w czasie tworzenia przed innej metody w `IBindingDisplay` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ce16b-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce16b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce16b-110">Requirements</span></span>  
 <span data-ttu-id="ce16b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce16b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce16b-112">**Nagłówek:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="ce16b-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="ce16b-113">**Biblioteka:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="ce16b-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="ce16b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce16b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce16b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce16b-115">See also</span></span>

- [<span data-ttu-id="ce16b-116">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce16b-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
