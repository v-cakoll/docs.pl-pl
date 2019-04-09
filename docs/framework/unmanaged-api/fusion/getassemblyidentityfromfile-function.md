---
title: GetAssemblyIdentityFromFile — Funkcja
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f5dd25ec2a6a1b0b5d6266c3d8e728bd128a9ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106317"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="32352-102">GetAssemblyIdentityFromFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="32352-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="32352-103">Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="32352-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32352-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32352-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="32352-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32352-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="32352-106">[in] Nieprawidłowa ścieżka do żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="32352-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="32352-107">[in] `IID` Interfejsu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="32352-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="32352-108">[out] Wskaźnik interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="32352-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32352-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32352-109">Requirements</span></span>  
 <span data-ttu-id="32352-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32352-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32352-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="32352-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="32352-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="32352-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32352-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32352-113">See also</span></span>

- [<span data-ttu-id="32352-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="32352-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="32352-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="32352-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
