---
title: "ICorRuntimeHost::MapFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3047a473f36762ec57ae4ea87067e941ac568c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="f3554-102">ICorRuntimeHost::MapFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3554-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="f3554-103">Mapuje określony plik do pamięci.</span><span class="sxs-lookup"><span data-stu-id="f3554-103">Maps the specified file into memory.</span></span> <span data-ttu-id="f3554-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f3554-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3554-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3554-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3554-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3554-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="f3554-107">[in] Dojście pliku można zamapować.</span><span class="sxs-lookup"><span data-stu-id="f3554-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="f3554-108">[out] Początkowy adres pamięci od którego należy zacząć mapowania pliku.</span><span class="sxs-lookup"><span data-stu-id="f3554-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3554-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3554-109">Requirements</span></span>  
 <span data-ttu-id="f3554-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3554-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3554-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3554-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3554-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3554-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3554-113">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f3554-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3554-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3554-114">See Also</span></span>  
 [<span data-ttu-id="f3554-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3554-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
