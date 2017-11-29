---
title: "IBindingDisplay::GetCurrentDisplay — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.GetCurrentDisplay
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4e9ba86efe44fdcfb717970bf664198068d89d36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="5b966-102">IBindingDisplay::GetCurrentDisplay — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b966-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="5b966-103">Zwraca bieżący powiązanie wyświetlane informacje.</span><span class="sxs-lookup"><span data-stu-id="5b966-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b966-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b966-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b966-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b966-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="5b966-106">[out, retval] Wskaźnik do obiektu safearray zawierający informacje o powiązaniu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="5b966-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b966-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b966-107">Remarks</span></span>  
 <span data-ttu-id="5b966-108">[IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metody musi mieć wcześniej zakończyło się pomyślnie, a program musi zostać zatrzymana przez debuger.</span><span class="sxs-lookup"><span data-stu-id="5b966-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="5b966-109">Obiekt wywołujący musi cofnąć zwróconego `SAFEARRAY` pamięci za pomocą [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span><span class="sxs-lookup"><span data-stu-id="5b966-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b966-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b966-110">Requirements</span></span>  
 <span data-ttu-id="5b966-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b966-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b966-112">**Nagłówek:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="5b966-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="5b966-113">**Biblioteka:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="5b966-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="5b966-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b966-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b966-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b966-115">See Also</span></span>  
 [<span data-ttu-id="5b966-116">IBindingDisplay — interfejs</span><span class="sxs-lookup"><span data-stu-id="5b966-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="5b966-117">InitializeForProcess — metoda</span><span class="sxs-lookup"><span data-stu-id="5b966-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
