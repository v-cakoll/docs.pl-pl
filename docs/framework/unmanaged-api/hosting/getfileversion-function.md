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
ms.openlocfilehash: b1f5508e9ee41d8670b43d5b219846237e11fc8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778143"
---
# <a name="getfileversion-function"></a><span data-ttu-id="32282-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="32282-102">GetFileVersion Function</span></span>
<span data-ttu-id="32282-103">Pobiera wspólnego języka wspólnego (CLR) informacje o wersji określonego pliku, przy użyciu określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="32282-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="32282-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="32282-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32282-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="32282-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32282-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="32282-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="32282-107">[in] Ścieżka pliku do badania.</span><span class="sxs-lookup"><span data-stu-id="32282-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="32282-108">[out w] Bufor przydzielony, aby uzyskać informacje o wersji, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="32282-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="32282-109">[in] Rozmiar w szerokich znaków z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="32282-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="32282-110">[out] Rozmiar w bajtach zwracanego `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="32282-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32282-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32282-111">Requirements</span></span>  
 <span data-ttu-id="32282-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32282-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32282-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32282-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32282-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32282-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32282-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32282-115">See also</span></span>

- [<span data-ttu-id="32282-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="32282-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
