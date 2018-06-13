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
ms.openlocfilehash: a6a9c5ff91989fc1ad7da4e23df0e80d9d74ec7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424979"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="94b5f-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="94b5f-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="94b5f-103">Wskazuje, czy zmienna jest generowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="94b5f-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94b5f-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="94b5f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="94b5f-105">Members</span></span>  
  
|<span data-ttu-id="94b5f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="94b5f-106">Member</span></span>|<span data-ttu-id="94b5f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="94b5f-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="94b5f-108">Wskazuje, że dany zmiennej jest, generowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="94b5f-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94b5f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94b5f-109">Requirements</span></span>  
 <span data-ttu-id="94b5f-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94b5f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b5f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94b5f-111">See Also</span></span>  
 [<span data-ttu-id="94b5f-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="94b5f-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
