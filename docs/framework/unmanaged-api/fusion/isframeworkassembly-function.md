---
title: "IsFrameworkAssembly — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 216a7221550cb6345b29b5ed9e45b13ce40eadf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="13105-102">IsFrameworkAssembly — Funkcja</span><span class="sxs-lookup"><span data-stu-id="13105-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="13105-103">Pobiera wartość wskazującą, czy jest zarządzana w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="13105-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13105-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13105-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13105-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13105-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="13105-106">[in] Nazwa zestawu do sprawdzenia.</span><span class="sxs-lookup"><span data-stu-id="13105-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="13105-107">[out] Wartość logiczna wskazująca, czy zestaw jest zarządzana.</span><span class="sxs-lookup"><span data-stu-id="13105-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="13105-108">[in] Uncanonicalized ciąg, który zawiera unikatową tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="13105-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="13105-109">[in] Rozmiar `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="13105-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13105-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13105-110">Remarks</span></span>  
 <span data-ttu-id="13105-111">`pwzAssemblyReference` Parametr jest wskaźnikiem do ciągu znaków, który zawiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="13105-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="13105-112">Jeśli ten zestaw jest częścią programu .NET Framework, `pbIsFrameworkAssembly` parametr będzie zawierać wartość logiczną `true`.</span><span class="sxs-lookup"><span data-stu-id="13105-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="13105-113">Jeśli nazwany zestaw nie jest częścią programu .NET Framework lub `pwzAssemblyReference` parametru nie nadaje nazwy zestawu `pbIsFrameworkAssembly` będzie zawierać wartość logiczną `false`.</span><span class="sxs-lookup"><span data-stu-id="13105-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13105-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13105-114">Requirements</span></span>  
 <span data-ttu-id="13105-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13105-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13105-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13105-116">See Also</span></span>  
 [<span data-ttu-id="13105-117">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="13105-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
