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
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134530"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="48d3e-102">GetAssemblyIdentityFromFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="48d3e-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="48d3e-103">Pobiera wskaźnik do obiektu `IUnknown` o określonym `IID` w zestawie w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="48d3e-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48d3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48d3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="48d3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48d3e-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="48d3e-106">podczas Prawidłowa ścieżka do żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="48d3e-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="48d3e-107">podczas `IID` interfejsu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="48d3e-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="48d3e-108">określoną Zwrócony wskaźnik interfejsu.</span><span class="sxs-lookup"><span data-stu-id="48d3e-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d3e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48d3e-109">Requirements</span></span>  
 <span data-ttu-id="48d3e-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48d3e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48d3e-111">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="48d3e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="48d3e-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d3e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d3e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48d3e-113">See also</span></span>

- [<span data-ttu-id="48d3e-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="48d3e-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="48d3e-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="48d3e-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
