---
title: CorSymVarFlag — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 86cac53508665c3c97caaa415d8d3c38660928bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448552"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="1a86d-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1a86d-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="1a86d-103">Wskazuje, czy zmienna jest generowana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="1a86d-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a86d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a86d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="1a86d-105">Members</span><span class="sxs-lookup"><span data-stu-id="1a86d-105">Members</span></span>  
  
|<span data-ttu-id="1a86d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1a86d-106">Member</span></span>|<span data-ttu-id="1a86d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1a86d-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="1a86d-108">Wskazuje, że dana zmienna jest generowana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="1a86d-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a86d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a86d-109">Requirements</span></span>  
 <span data-ttu-id="1a86d-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1a86d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a86d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a86d-111">See also</span></span>

- [<span data-ttu-id="1a86d-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="1a86d-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
