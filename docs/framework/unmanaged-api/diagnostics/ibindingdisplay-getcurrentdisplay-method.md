---
title: IBindingDisplay::GetCurrentDisplay — Metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 472e06c3a00762a7bb012fbcb525d8e0b3a9271a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599523"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="651da-102">IBindingDisplay::GetCurrentDisplay — Metoda</span><span class="sxs-lookup"><span data-stu-id="651da-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="651da-103">Zwraca bieżące informacje wyświetlania powiązania.</span><span class="sxs-lookup"><span data-stu-id="651da-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="651da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="651da-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="651da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="651da-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="651da-106">[out, retval] Wskaźnik do obiektu safearray zawierający powiązania wyświetlane informacje.</span><span class="sxs-lookup"><span data-stu-id="651da-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="651da-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="651da-107">Remarks</span></span>  
 <span data-ttu-id="651da-108">[IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musi mieć wcześniej zakończyło się pomyślnie, a program musi zostać zatrzymana przez debuger.</span><span class="sxs-lookup"><span data-stu-id="651da-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="651da-109">Obiekt wywołujący musi deallocate zwracanego `SAFEARRAY` pamięci za pomocą [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="651da-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="651da-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="651da-110">Requirements</span></span>  
 <span data-ttu-id="651da-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="651da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="651da-112">**Nagłówek:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="651da-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="651da-113">**Biblioteka:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="651da-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="651da-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="651da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="651da-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="651da-115">See also</span></span>

- [<span data-ttu-id="651da-116">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="651da-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="651da-117">InitializeForProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="651da-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
