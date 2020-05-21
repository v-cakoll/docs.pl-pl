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
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762672"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="aa2ce-102">ICorRuntimeHost::MapFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa2ce-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="aa2ce-103">Mapuje określony plik do pamięci.</span><span class="sxs-lookup"><span data-stu-id="aa2ce-103">Maps the specified file into memory.</span></span> <span data-ttu-id="aa2ce-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="aa2ce-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa2ce-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa2ce-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa2ce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa2ce-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="aa2ce-107">podczas Dojście pliku do zmapowania.</span><span class="sxs-lookup"><span data-stu-id="aa2ce-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="aa2ce-108">określoną Początkowy adres pamięci, pod którym ma zostać rozpoczęte mapowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="aa2ce-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa2ce-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa2ce-109">Requirements</span></span>  
 <span data-ttu-id="aa2ce-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa2ce-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa2ce-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa2ce-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa2ce-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa2ce-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa2ce-113">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="aa2ce-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2ce-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa2ce-114">See also</span></span>

- [<span data-ttu-id="aa2ce-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa2ce-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
