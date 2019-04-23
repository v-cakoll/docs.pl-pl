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
ms.openlocfilehash: 0c797378f5e13f39c1c786237a3a7b9cf577fccc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198858"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="a7130-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a7130-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="a7130-103">Wskazuje, czy zmienna jest generowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="a7130-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7130-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7130-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="a7130-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a7130-105">Members</span></span>  
  
|<span data-ttu-id="a7130-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a7130-106">Member</span></span>|<span data-ttu-id="a7130-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a7130-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="a7130-108">Wskazuje, że danego zmiennej jest generowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="a7130-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7130-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7130-109">Requirements</span></span>  
 <span data-ttu-id="a7130-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a7130-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7130-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7130-111">See also</span></span>

- [<span data-ttu-id="a7130-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="a7130-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
