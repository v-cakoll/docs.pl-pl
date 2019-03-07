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
ms.openlocfilehash: a6b5aa78efcc19f1fc50c8e9bfc5105f9afd7d50
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495211"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="ee0f6-102">CreateApplicationContext — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ee0f6-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="ee0f6-103">Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ee0f6-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee0f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee0f6-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee0f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee0f6-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="ee0f6-106">[in] Wskaźnik do przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ee0f6-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="ee0f6-107">[out] Wskaźnik do kontekstu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee0f6-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee0f6-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee0f6-108">Requirements</span></span>  
 <span data-ttu-id="ee0f6-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee0f6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee0f6-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ee0f6-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ee0f6-111">**Biblioteka:** Dołączony jako zasób w Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="ee0f6-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="ee0f6-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee0f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee0f6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee0f6-113">See also</span></span>
- [<span data-ttu-id="ee0f6-114">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee0f6-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="ee0f6-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="ee0f6-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="ee0f6-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="ee0f6-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
