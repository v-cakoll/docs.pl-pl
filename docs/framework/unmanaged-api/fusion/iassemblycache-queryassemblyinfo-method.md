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
ms.openlocfilehash: 08b9fdee1138becd4cd5a933f96021c470aadf1f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796787"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="fcb23-102">IAssemblyCache::QueryAssemblyInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="fcb23-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="fcb23-103">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fcb23-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcb23-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcb23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcb23-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="fcb23-106">podczas Flagi zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="fcb23-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="fcb23-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="fcb23-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="fcb23-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="fcb23-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="fcb23-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="fcb23-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="fcb23-110">podczas Nazwa zestawu, dla którego zostaną pobrane dane.</span><span class="sxs-lookup"><span data-stu-id="fcb23-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="fcb23-111">[in. out] Struktura [ASSEMBLY_INFO](assembly-info-structure.md) , która zawiera dane dotyczące zestawu.</span><span class="sxs-lookup"><span data-stu-id="fcb23-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcb23-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcb23-112">Requirements</span></span>  
 <span data-ttu-id="fcb23-113">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb23-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcb23-114">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="fcb23-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fcb23-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcb23-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb23-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcb23-116">See also</span></span>

- [<span data-ttu-id="fcb23-117">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="fcb23-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
