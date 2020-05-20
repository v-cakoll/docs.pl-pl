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
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442153"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="6498f-102">IBindingDisplay::InitializeForProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="6498f-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="6498f-103">Inicjuje obiekt [IBindingDisplay](ibindingdisplay-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6498f-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6498f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6498f-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6498f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6498f-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="6498f-106">podczas Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="6498f-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6498f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6498f-107">Remarks</span></span>  
 <span data-ttu-id="6498f-108">Debuger wywołuje `InitializeForProcess` metodę w czasie tworzenia w celu zainicjowania wyświetlania powiązania.</span><span class="sxs-lookup"><span data-stu-id="6498f-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="6498f-109">`InitializeForProcess`musi być wywoływana w czasie tworzenia przed wywołaniem innej metody na `IBindingDisplay` .</span><span class="sxs-lookup"><span data-stu-id="6498f-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6498f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6498f-110">Requirements</span></span>  
 <span data-ttu-id="6498f-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6498f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6498f-112">**Nagłówek:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="6498f-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="6498f-113">**Biblioteka:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="6498f-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="6498f-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6498f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6498f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6498f-115">See also</span></span>

- [<span data-ttu-id="6498f-116">IBindingDisplay — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6498f-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
