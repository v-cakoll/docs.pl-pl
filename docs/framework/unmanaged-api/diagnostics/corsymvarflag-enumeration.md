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
ms.openlocfilehash: 21e92d8f2fb80c4c41d516ef281bf4fc8a75f4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176646"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="f6e39-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f6e39-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="f6e39-103">Wskazuje, czy zmienna jest generowana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="f6e39-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6e39-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="f6e39-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f6e39-105">Members</span></span>  
  
|<span data-ttu-id="f6e39-106">Członek</span><span class="sxs-lookup"><span data-stu-id="f6e39-106">Member</span></span>|<span data-ttu-id="f6e39-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e39-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="f6e39-108">Wskazuje, że dana zmienna jest generowana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="f6e39-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6e39-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6e39-109">Requirements</span></span>  
 <span data-ttu-id="f6e39-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f6e39-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e39-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6e39-111">See also</span></span>

- [<span data-ttu-id="f6e39-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="f6e39-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
