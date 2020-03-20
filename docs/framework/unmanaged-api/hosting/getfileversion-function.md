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
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178178"
---
# <a name="getfileversion-function"></a><span data-ttu-id="281ea-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="281ea-102">GetFileVersion Function</span></span>
<span data-ttu-id="281ea-103">Pobiera informacje o wersji wspólnego środowiska wykonawczego języka (CLR) określonego pliku przy użyciu określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="281ea-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="281ea-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="281ea-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="281ea-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="281ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="281ea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="281ea-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="281ea-107">[w] Ścieżka pliku, który ma zostać zbadany.</span><span class="sxs-lookup"><span data-stu-id="281ea-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="281ea-108">[w, na zewnątrz] Bufor przydzielony dla zwracanych informacji o wersji.</span><span class="sxs-lookup"><span data-stu-id="281ea-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="281ea-109">[w] Rozmiar, w szerokich `szBuffer`znaków, z .</span><span class="sxs-lookup"><span data-stu-id="281ea-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="281ea-110">[na zewnątrz] Rozmiar (w bajtach) `szBuffer`zwracanego .</span><span class="sxs-lookup"><span data-stu-id="281ea-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="281ea-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="281ea-111">Requirements</span></span>  
 <span data-ttu-id="281ea-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="281ea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="281ea-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="281ea-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="281ea-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="281ea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="281ea-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="281ea-115">See also</span></span>

- [<span data-ttu-id="281ea-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="281ea-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
