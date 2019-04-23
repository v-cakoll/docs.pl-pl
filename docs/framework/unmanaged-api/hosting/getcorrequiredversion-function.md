---
title: GetCORRequiredVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5786444c36fcfc9547be1db0006757b0a9376c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175191"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="0a418-102">GetCORRequiredVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0a418-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="0a418-103">Pobiera wymagane wspólnego języka wspólnego (CLR) numer wersji.</span><span class="sxs-lookup"><span data-stu-id="0a418-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="0a418-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a418-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a418-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a418-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a418-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a418-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="0a418-107">[out] Bufor, zawierających ciąg, który określa numer wersji.</span><span class="sxs-lookup"><span data-stu-id="0a418-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="0a418-108">[in] Rozmiar w bajtach rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="0a418-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0a418-109">[out] Liczba bajtów zwróconych w buforze.</span><span class="sxs-lookup"><span data-stu-id="0a418-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a418-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a418-110">Requirements</span></span>  
 <span data-ttu-id="0a418-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a418-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a418-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a418-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a418-113">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a418-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a418-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a418-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a418-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a418-115">See also</span></span>

- [<span data-ttu-id="0a418-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="0a418-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
