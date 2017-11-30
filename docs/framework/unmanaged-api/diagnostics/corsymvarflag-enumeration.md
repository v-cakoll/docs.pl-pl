---
title: "CorSymVarFlag — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymVarFlag
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymVarFlag
helpviewer_keywords: CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: edbbc8109eb44494c7f4fac0ed8756e23bdc955b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="456c6-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="456c6-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="456c6-103">Wskazuje, czy zmienna jest generowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="456c6-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="456c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="456c6-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="456c6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="456c6-105">Members</span></span>  
  
|<span data-ttu-id="456c6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="456c6-106">Member</span></span>|<span data-ttu-id="456c6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="456c6-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="456c6-108">Wskazuje, że dany zmiennej jest, generowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="456c6-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="456c6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="456c6-109">Requirements</span></span>  
 <span data-ttu-id="456c6-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="456c6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456c6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="456c6-111">See Also</span></span>  
 [<span data-ttu-id="456c6-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="456c6-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
