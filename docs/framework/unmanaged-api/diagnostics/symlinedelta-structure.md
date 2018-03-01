---
title: "SYMLINEDELTA — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 677b7c2858e4f3248e0d46e460b9eef09de724f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="16a19-102">SYMLINEDELTA — Struktura</span><span class="sxs-lookup"><span data-stu-id="16a19-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="16a19-103">Zawiera informacje metod, które zostały przeniesione w wyniku zmiany do obsługi symboli.</span><span class="sxs-lookup"><span data-stu-id="16a19-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16a19-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="16a19-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="16a19-105">Members</span></span>  
  
|<span data-ttu-id="16a19-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="16a19-106">Member</span></span>|<span data-ttu-id="16a19-107">Opis</span><span class="sxs-lookup"><span data-stu-id="16a19-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="16a19-108">Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="16a19-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="16a19-109">Liczba wierszy, które metody została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="16a19-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16a19-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16a19-110">Requirements</span></span>  
 <span data-ttu-id="16a19-111">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="16a19-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a19-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16a19-112">See Also</span></span>  
 [<span data-ttu-id="16a19-113">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="16a19-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
