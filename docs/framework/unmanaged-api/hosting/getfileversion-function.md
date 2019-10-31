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
ms.openlocfilehash: f197c8802bd9e55391b3e3e20c64398736070a16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136336"
---
# <a name="getfileversion-function"></a><span data-ttu-id="4b24c-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4b24c-102">GetFileVersion Function</span></span>
<span data-ttu-id="4b24c-103">Pobiera informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) określonego pliku przy użyciu określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="4b24c-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="4b24c-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4b24c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b24c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b24c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b24c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b24c-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="4b24c-107">podczas Ścieżka pliku, który ma zostać zbadany.</span><span class="sxs-lookup"><span data-stu-id="4b24c-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="4b24c-108">[in. out] Bufor przydzielony dla zwracanych informacji o wersji.</span><span class="sxs-lookup"><span data-stu-id="4b24c-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4b24c-109">podczas Rozmiar, w postaci znaków dwubajtowych, `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4b24c-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="4b24c-110">określoną Rozmiar w bajtach zwracanej `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4b24c-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b24c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b24c-111">Requirements</span></span>  
 <span data-ttu-id="4b24c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b24c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b24c-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b24c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b24c-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b24c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b24c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b24c-115">See also</span></span>

- [<span data-ttu-id="4b24c-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="4b24c-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
