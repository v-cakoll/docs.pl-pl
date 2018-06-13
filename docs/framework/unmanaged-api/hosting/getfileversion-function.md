---
title: GetFileVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b772de720a8c3b669bd3cbe9591637d931cb8763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430622"
---
# <a name="getfileversion-function"></a><span data-ttu-id="8a291-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8a291-102">GetFileVersion Function</span></span>
<span data-ttu-id="8a291-103">Pobiera wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) informacje o wersji określonego pliku, używając określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="8a291-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="8a291-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a291-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a291-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a291-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a291-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a291-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="8a291-107">[in] Ścieżka pliku, który ma być zbadana.</span><span class="sxs-lookup"><span data-stu-id="8a291-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="8a291-108">[w, out] Bufor przydzielony informacje o wersji, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="8a291-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="8a291-109">[in] Rozmiar w znaki dwubajtowe z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8a291-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8a291-110">[out] Rozmiar w bajtach, zwracana `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8a291-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a291-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a291-111">Requirements</span></span>  
 <span data-ttu-id="8a291-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a291-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a291-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a291-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a291-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a291-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a291-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a291-115">See Also</span></span>  
 [<span data-ttu-id="8a291-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="8a291-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
