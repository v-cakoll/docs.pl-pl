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
ms.openlocfilehash: d98829b29100824e5d606e23aaf287c9f6e81d69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771920"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="a7870-102">CreateApplicationContext — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a7870-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="a7870-103">Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a7870-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7870-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7870-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7870-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7870-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="a7870-106">[in] Wskaźnik do przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a7870-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="a7870-107">[out] Wskaźnik do kontekstu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7870-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7870-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7870-108">Requirements</span></span>  
 <span data-ttu-id="a7870-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7870-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7870-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a7870-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a7870-111">**Biblioteka:** Dołączony jako zasób w Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="a7870-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="a7870-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7870-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7870-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7870-113">See also</span></span>

- [<span data-ttu-id="a7870-114">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7870-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="a7870-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="a7870-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="a7870-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="a7870-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
