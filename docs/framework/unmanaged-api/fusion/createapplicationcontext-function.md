---
title: CreateApplicationContext — Funkcja
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 709769c336d875ee5ddd00b4e1cf919c61e2c394
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746625"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="45af2-102">CreateApplicationContext — Funkcja</span><span class="sxs-lookup"><span data-stu-id="45af2-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="45af2-103">Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="45af2-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45af2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45af2-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45af2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45af2-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="45af2-106">[in] Wskaźnik do przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="45af2-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="45af2-107">[out] Wskaźnik do kontekstu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45af2-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45af2-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45af2-108">Requirements</span></span>  
 <span data-ttu-id="45af2-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45af2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45af2-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="45af2-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="45af2-111">**Biblioteka:** Dołączony jako zasób w Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="45af2-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="45af2-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45af2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45af2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45af2-113">See also</span></span>
- [<span data-ttu-id="45af2-114">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="45af2-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="45af2-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="45af2-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="45af2-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="45af2-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
