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
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442192"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="87ba2-102">IBindingDisplay::GetCurrentDisplay — Metoda</span><span class="sxs-lookup"><span data-stu-id="87ba2-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="87ba2-103">Zwraca bieżące informacje o wyświetlaniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="87ba2-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ba2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87ba2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ba2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87ba2-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="87ba2-106">[out, retval] Wskaźnik do elementu SAFEARRAY zawierającego informacje o wyświetlaniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="87ba2-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ba2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87ba2-107">Remarks</span></span>  
 <span data-ttu-id="87ba2-108">Metoda [IBindingDisplay:: InitializeForProcess —](ibindingdisplay-initializeforprocess-method.md) musi być wcześniej zakończona pomyślnie, a program musi być zatrzymany przez debuger.</span><span class="sxs-lookup"><span data-stu-id="87ba2-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="87ba2-109">Obiekt wywołujący musi cofnąć alokację zwróconej `SAFEARRAY` pamięci za pomocą [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="87ba2-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ba2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87ba2-110">Requirements</span></span>  
 <span data-ttu-id="87ba2-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ba2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ba2-112">**Nagłówek:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="87ba2-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="87ba2-113">**Biblioteka:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="87ba2-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="87ba2-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ba2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ba2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87ba2-115">See also</span></span>

- [<span data-ttu-id="87ba2-116">IBindingDisplay — Interfejs</span><span class="sxs-lookup"><span data-stu-id="87ba2-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="87ba2-117">InitializeForProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="87ba2-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
