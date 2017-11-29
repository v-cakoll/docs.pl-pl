---
title: "CreateApplicationContext — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateApplicationContext
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateApplicationContext
helpviewer_keywords: CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c089c32d4bc8474168274186a9303d39976abfca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="a5850-102">CreateApplicationContext — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a5850-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="a5850-103">Ta funkcja obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a5850-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5850-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5850-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5850-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5850-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="a5850-106">[in] Wskaźnik do przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="a5850-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="a5850-107">[out] Wskaźnik do kontekstu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5850-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5850-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5850-108">Requirements</span></span>  
 <span data-ttu-id="a5850-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5850-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5850-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a5850-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a5850-111">**Biblioteka:** uwzględnione jako zasób w Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="a5850-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="a5850-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5850-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5850-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5850-113">See Also</span></span>  
 [<span data-ttu-id="a5850-114">IAssemblyCache — interfejs</span><span class="sxs-lookup"><span data-stu-id="a5850-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="a5850-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="a5850-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="a5850-116">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="a5850-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
