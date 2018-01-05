---
title: "GetCORRequiredVersion — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORRequiredVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetCORRequiredVersion
helpviewer_keywords: GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65505243d7d1691f0458d614fd878b054916f113
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="d7388-102">GetCORRequiredVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d7388-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="d7388-103">Pobiera wymagane wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) numer wersji.</span><span class="sxs-lookup"><span data-stu-id="d7388-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="d7388-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7388-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7388-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7388-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7388-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7388-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="d7388-107">[out] Bufor zawierający ciąg, który określa numer wersji.</span><span class="sxs-lookup"><span data-stu-id="d7388-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d7388-108">[in] Rozmiar w bajtach buforu.</span><span class="sxs-lookup"><span data-stu-id="d7388-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d7388-109">[out] Liczba bajtów zwrócona w buforze.</span><span class="sxs-lookup"><span data-stu-id="d7388-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7388-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7388-110">Requirements</span></span>  
 <span data-ttu-id="d7388-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7388-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7388-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7388-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7388-113">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7388-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7388-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7388-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7388-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7388-115">See Also</span></span>  
 [<span data-ttu-id="d7388-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d7388-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
