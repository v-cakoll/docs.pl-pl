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
ms.openlocfilehash: 05267819a1c61c55220f477173069ddf51edaeb4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="45638-102">GetCORRequiredVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="45638-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="45638-103">Pobiera wymagane wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) numer wersji.</span><span class="sxs-lookup"><span data-stu-id="45638-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="45638-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45638-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45638-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="45638-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45638-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="45638-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="45638-107">[out] Bufor zawierający ciąg, który określa numer wersji.</span><span class="sxs-lookup"><span data-stu-id="45638-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="45638-108">[in] Rozmiar w bajtach buforu.</span><span class="sxs-lookup"><span data-stu-id="45638-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="45638-109">[out] Liczba bajtów zwrócona w buforze.</span><span class="sxs-lookup"><span data-stu-id="45638-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45638-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45638-110">Requirements</span></span>  
 <span data-ttu-id="45638-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45638-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45638-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="45638-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45638-113">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45638-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45638-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45638-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45638-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45638-115">See Also</span></span>  
 [<span data-ttu-id="45638-116">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="45638-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
