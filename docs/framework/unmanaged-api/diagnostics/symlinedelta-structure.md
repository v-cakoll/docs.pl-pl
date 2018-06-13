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
ms.openlocfilehash: 77cd8b7d791d11f6d40386f4747c60cd4832521a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428097"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="e150f-102">SYMLINEDELTA — Struktura</span><span class="sxs-lookup"><span data-stu-id="e150f-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="e150f-103">Zawiera informacje metod, które zostały przeniesione w wyniku zmiany do obsługi symboli.</span><span class="sxs-lookup"><span data-stu-id="e150f-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e150f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e150f-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="e150f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e150f-105">Members</span></span>  
  
|<span data-ttu-id="e150f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e150f-106">Member</span></span>|<span data-ttu-id="e150f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e150f-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="e150f-108">Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="e150f-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="e150f-109">Liczba wierszy, które metody została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="e150f-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e150f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e150f-110">Requirements</span></span>  
 <span data-ttu-id="e150f-111">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="e150f-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e150f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e150f-112">See Also</span></span>  
 [<span data-ttu-id="e150f-113">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e150f-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
