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
ms.openlocfilehash: 9294dbf1caddd4b607185de54efd2b4764e6ca35
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448503"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="c8b87-102">IBindingDisplay::GetCurrentDisplay — Metoda</span><span class="sxs-lookup"><span data-stu-id="c8b87-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="c8b87-103">Zwraca bieżące informacje o wyświetlaniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8b87-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8b87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8b87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8b87-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="c8b87-106">[out, retval] Wskaźnik do elementu SAFEARRAY zawierającego informacje o wyświetlaniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8b87-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8b87-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8b87-107">Remarks</span></span>  
 <span data-ttu-id="c8b87-108">Metoda [IBindingDisplay:: InitializeForProcess —](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) musi być wcześniej zakończona pomyślnie, a program musi być zatrzymany przez debuger.</span><span class="sxs-lookup"><span data-stu-id="c8b87-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="c8b87-109">Obiekt wywołujący musi cofnąć alokację zwróconej pamięci `SAFEARRAY` przy użyciu [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="c8b87-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b87-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8b87-110">Requirements</span></span>  
 <span data-ttu-id="c8b87-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b87-112">**Nagłówek:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="c8b87-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="c8b87-113">**Biblioteka:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="c8b87-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="c8b87-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b87-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8b87-115">See also</span></span>

- [<span data-ttu-id="c8b87-116">IBindingDisplay, interfejs</span><span class="sxs-lookup"><span data-stu-id="c8b87-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="c8b87-117">InitializeForProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="c8b87-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
