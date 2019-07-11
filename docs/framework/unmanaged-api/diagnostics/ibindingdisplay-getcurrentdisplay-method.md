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
ms.openlocfilehash: d075aeeb904469613999829a1444511d069b9918
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775980"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="b95ba-102">IBindingDisplay::GetCurrentDisplay — Metoda</span><span class="sxs-lookup"><span data-stu-id="b95ba-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="b95ba-103">Zwraca bieżące informacje wyświetlania powiązania.</span><span class="sxs-lookup"><span data-stu-id="b95ba-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b95ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b95ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b95ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b95ba-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="b95ba-106">[out, retval] Wskaźnik do obiektu safearray zawierający powiązania wyświetlane informacje.</span><span class="sxs-lookup"><span data-stu-id="b95ba-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b95ba-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b95ba-107">Remarks</span></span>  
 <span data-ttu-id="b95ba-108">[IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musi mieć wcześniej zakończyło się pomyślnie, a program musi zostać zatrzymana przez debuger.</span><span class="sxs-lookup"><span data-stu-id="b95ba-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="b95ba-109">Obiekt wywołujący musi deallocate zwracanego `SAFEARRAY` pamięci za pomocą [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="b95ba-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b95ba-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b95ba-110">Requirements</span></span>  
 <span data-ttu-id="b95ba-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b95ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b95ba-112">**Nagłówek:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="b95ba-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="b95ba-113">**Biblioteka:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="b95ba-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="b95ba-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b95ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95ba-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b95ba-115">See also</span></span>

- [<span data-ttu-id="b95ba-116">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="b95ba-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="b95ba-117">InitializeForProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="b95ba-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
