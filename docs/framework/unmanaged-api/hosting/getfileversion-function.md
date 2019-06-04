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
ms.openlocfilehash: bf63b2641c4140b287a3932c2073b445211ad3aa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490368"
---
# <a name="getfileversion-function"></a><span data-ttu-id="a9c88-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a9c88-102">GetFileVersion Function</span></span>
<span data-ttu-id="a9c88-103">Pobiera wspólnego języka wspólnego (CLR) informacje o wersji określonego pliku, przy użyciu określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="a9c88-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="a9c88-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a9c88-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c88-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9c88-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9c88-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9c88-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="a9c88-107">[in] Ścieżka pliku do badania.</span><span class="sxs-lookup"><span data-stu-id="a9c88-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a9c88-108">[out w] Bufor przydzielony, aby uzyskać informacje o wersji, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="a9c88-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a9c88-109">[in] Rozmiar w szerokich znaków z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a9c88-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a9c88-110">[out] Rozmiar w bajtach zwracanego `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a9c88-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9c88-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9c88-111">Requirements</span></span>  
 <span data-ttu-id="a9c88-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9c88-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9c88-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9c88-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9c88-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9c88-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c88-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9c88-115">See also</span></span>

- [<span data-ttu-id="a9c88-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a9c88-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
