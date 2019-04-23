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
ms.openlocfilehash: d25a3ccdd66ff7acb70f1f5e6c60157b53cc97c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123737"
---
# <a name="getfileversion-function"></a><span data-ttu-id="2c5d7-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2c5d7-102">GetFileVersion Function</span></span>
<span data-ttu-id="2c5d7-103">Pobiera wspólnego języka wspólnego (CLR) informacje o wersji określonego pliku, przy użyciu określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="2c5d7-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="2c5d7-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c5d7-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c5d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c5d7-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c5d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c5d7-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="2c5d7-107">[in] Ścieżka pliku do badania.</span><span class="sxs-lookup"><span data-stu-id="2c5d7-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2c5d7-108">[out w] Bufor przydzielony, aby uzyskać informacje o wersji, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="2c5d7-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2c5d7-109">[in] Rozmiar w szerokich znaków z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2c5d7-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2c5d7-110">[out] Rozmiar w bajtach zwracanego `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2c5d7-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c5d7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c5d7-111">Requirements</span></span>  
 <span data-ttu-id="2c5d7-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c5d7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c5d7-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c5d7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c5d7-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c5d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5d7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c5d7-115">See also</span></span>

- [<span data-ttu-id="2c5d7-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2c5d7-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
