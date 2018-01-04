---
title: "GetAssemblyIdentityFromFile — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyIdentityFromFile
helpviewer_keywords: GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56d7fb4ee74e40ecd29ee276665ff43ab9fd56be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="72e4f-102">GetAssemblyIdentityFromFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="72e4f-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="72e4f-103">Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie przy użyciu określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="72e4f-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72e4f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72e4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72e4f-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="72e4f-106">[in] Nieprawidłowa ścieżka żądany zestaw.</span><span class="sxs-lookup"><span data-stu-id="72e4f-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="72e4f-107">[in] `IID` Interfejsu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="72e4f-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="72e4f-108">[out] Wskaźnik interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="72e4f-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e4f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72e4f-109">Requirements</span></span>  
 <span data-ttu-id="72e4f-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72e4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72e4f-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="72e4f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="72e4f-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72e4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e4f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72e4f-113">See Also</span></span>  
 <span data-ttu-id="72e4f-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="72e4f-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="72e4f-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="72e4f-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
