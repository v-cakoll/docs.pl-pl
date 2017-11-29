---
title: "GetFileVersion — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetFileVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetFileVersion
helpviewer_keywords: GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654cda723db9910fb80d32bc08c393a44f04b586
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getfileversion-function"></a><span data-ttu-id="40889-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="40889-102">GetFileVersion Function</span></span>
<span data-ttu-id="40889-103">Pobiera wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) informacje o wersji określonego pliku, używając określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="40889-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="40889-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40889-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40889-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="40889-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40889-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40889-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="40889-107">[in] Ścieżka pliku, który ma być zbadana.</span><span class="sxs-lookup"><span data-stu-id="40889-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="40889-108">[w, out] Bufor przydzielony informacje o wersji, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="40889-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="40889-109">[in] Rozmiar w znaki dwubajtowe z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="40889-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="40889-110">[out] Rozmiar w bajtach, zwracana `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="40889-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40889-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40889-111">Requirements</span></span>  
 <span data-ttu-id="40889-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40889-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40889-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40889-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40889-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40889-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40889-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40889-115">See Also</span></span>  
 [<span data-ttu-id="40889-116">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="40889-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
