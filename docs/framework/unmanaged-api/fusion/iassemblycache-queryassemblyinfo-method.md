---
title: IAssemblyCache::QueryAssemblyInfo — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6935a72bb99e636b3732958ee88ad224b401513b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430723"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="049a9-102">IAssemblyCache::QueryAssemblyInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="049a9-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="049a9-103">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="049a9-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="049a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="049a9-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="049a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="049a9-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="049a9-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="049a9-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="049a9-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="049a9-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="049a9-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="049a9-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="049a9-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="049a9-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="049a9-110">[in] Nazwa zestawu, dla którego będzie można pobrać danych.</span><span class="sxs-lookup"><span data-stu-id="049a9-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="049a9-111">[w, out] [Assembly_info —](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) strukturę, która zawiera dane dotyczące zestawu.</span><span class="sxs-lookup"><span data-stu-id="049a9-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="049a9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="049a9-112">Requirements</span></span>  
 <span data-ttu-id="049a9-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="049a9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="049a9-114">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="049a9-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="049a9-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="049a9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="049a9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="049a9-116">See Also</span></span>  
 [<span data-ttu-id="049a9-117">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="049a9-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
