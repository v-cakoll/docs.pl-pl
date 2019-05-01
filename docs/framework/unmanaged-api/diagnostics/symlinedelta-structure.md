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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914644"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="e5e12-102">SYMLINEDELTA — Struktura</span><span class="sxs-lookup"><span data-stu-id="e5e12-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="e5e12-103">Zawiera informacje o metodach, które zostały przeniesione w wyniku zmiany obsługi symboli.</span><span class="sxs-lookup"><span data-stu-id="e5e12-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5e12-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="e5e12-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e5e12-105">Members</span></span>  
  
|<span data-ttu-id="e5e12-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e5e12-106">Member</span></span>|<span data-ttu-id="e5e12-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e12-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="e5e12-108">Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="e5e12-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="e5e12-109">Liczba wierszy, które metody została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="e5e12-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5e12-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5e12-110">Requirements</span></span>  
 <span data-ttu-id="e5e12-111">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="e5e12-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e12-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5e12-112">See also</span></span>

- [<span data-ttu-id="e5e12-113">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e5e12-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
