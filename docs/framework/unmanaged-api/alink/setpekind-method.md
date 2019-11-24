---
title: SetPEKind — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445533"
---
# <a name="setpekind-method"></a><span data-ttu-id="b66c8-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="b66c8-102">SetPEKind Method</span></span>
<span data-ttu-id="b66c8-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span><span class="sxs-lookup"><span data-stu-id="b66c8-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b66c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b66c8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="b66c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b66c8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b66c8-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="b66c8-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b66c8-107">Token of file for which the PE type is to be set.</span><span class="sxs-lookup"><span data-stu-id="b66c8-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="b66c8-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span><span class="sxs-lookup"><span data-stu-id="b66c8-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="b66c8-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b66c8-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="b66c8-110">The target machine architecture, as indicated in the NT header.</span><span class="sxs-lookup"><span data-stu-id="b66c8-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b66c8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b66c8-111">Return Value</span></span>  
 <span data-ttu-id="b66c8-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="b66c8-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b66c8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b66c8-113">Requirements</span></span>  
 <span data-ttu-id="b66c8-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="b66c8-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66c8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b66c8-115">See also</span></span>

- [<span data-ttu-id="b66c8-116">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="b66c8-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="b66c8-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b66c8-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b66c8-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="b66c8-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b66c8-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="b66c8-119">ALink API</span></span>](index.md)
