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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50367358ba5bcf335f8cc2ca3222f6cf7ea2ff70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670143"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="7f612-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7f612-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="7f612-103">Wskazuje, czy zmienna jest generowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="7f612-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f612-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f612-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="7f612-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7f612-105">Members</span></span>  
  
|<span data-ttu-id="7f612-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7f612-106">Member</span></span>|<span data-ttu-id="7f612-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7f612-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="7f612-108">Wskazuje, że danego zmiennej jest generowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="7f612-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f612-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f612-109">Requirements</span></span>  
 <span data-ttu-id="7f612-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f612-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f612-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f612-111">See also</span></span>
- [<span data-ttu-id="7f612-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="7f612-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
