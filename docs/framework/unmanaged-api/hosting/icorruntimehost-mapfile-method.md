---
title: ICorRuntimeHost::MapFile — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8a979e86dbe52577d0b58089015338e4a87750d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193879"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="4d70c-102">ICorRuntimeHost::MapFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d70c-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="4d70c-103">Mapuje określony plik do pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d70c-103">Maps the specified file into memory.</span></span> <span data-ttu-id="4d70c-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="4d70c-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d70c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d70c-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d70c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d70c-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="4d70c-107">[in] Uchwyt pliku, które mają być mapowane.</span><span class="sxs-lookup"><span data-stu-id="4d70c-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="4d70c-108">[out] Początkowy adres pamięci, od którego należy rozpocząć mapowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="4d70c-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d70c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d70c-109">Requirements</span></span>  
 <span data-ttu-id="4d70c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d70c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d70c-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4d70c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d70c-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d70c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d70c-113">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="4d70c-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d70c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d70c-114">See also</span></span>

- [<span data-ttu-id="4d70c-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d70c-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
