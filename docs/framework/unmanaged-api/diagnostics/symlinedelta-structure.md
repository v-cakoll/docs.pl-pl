---
title: SYMLINEDELTA — Struktura
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159487"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="12ac9-102">SYMLINEDELTA — Struktura</span><span class="sxs-lookup"><span data-stu-id="12ac9-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="12ac9-103">Zawiera informacje o metodach, które zostały przeniesione w wyniku zmiany obsługi symboli.</span><span class="sxs-lookup"><span data-stu-id="12ac9-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ac9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12ac9-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="12ac9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="12ac9-105">Members</span></span>  
  
|<span data-ttu-id="12ac9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="12ac9-106">Member</span></span>|<span data-ttu-id="12ac9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="12ac9-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="12ac9-108">Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="12ac9-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="12ac9-109">Liczba wierszy, które metody została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="12ac9-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12ac9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12ac9-110">Requirements</span></span>  
 <span data-ttu-id="12ac9-111">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="12ac9-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ac9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12ac9-112">See also</span></span>

- [<span data-ttu-id="12ac9-113">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="12ac9-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
