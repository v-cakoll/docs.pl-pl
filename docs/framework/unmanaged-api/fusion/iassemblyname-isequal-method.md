---
title: IAssemblyName::IsEqual — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134304"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="d3ff5-102">IAssemblyName::IsEqual — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3ff5-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="d3ff5-103">Określa, czy określony obiekt [IAssemblyName](iassemblyname-interface.md) jest równy temu `IAssemblyName`, na podstawie określonych flag porównania.</span><span class="sxs-lookup"><span data-stu-id="d3ff5-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ff5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3ff5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3ff5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3ff5-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d3ff5-106">podczas Obiekt `IAssemblyName`, do którego mają zostać porównane `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="d3ff5-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="d3ff5-107">podczas Bitowa kombinacja wartości [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) , które mają wpływ na porównanie.</span><span class="sxs-lookup"><span data-stu-id="d3ff5-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3ff5-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3ff5-108">Requirements</span></span>  
 <span data-ttu-id="d3ff5-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3ff5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ff5-110">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d3ff5-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d3ff5-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ff5-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ff5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3ff5-112">See also</span></span>

- [<span data-ttu-id="d3ff5-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3ff5-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="d3ff5-114">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="d3ff5-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
