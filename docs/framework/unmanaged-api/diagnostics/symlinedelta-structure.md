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
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609303"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="4dfa3-102">SYMLINEDELTA — Struktura</span><span class="sxs-lookup"><span data-stu-id="4dfa3-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="4dfa3-103">Zawiera informacje do obsługi symboli dotyczące metod, które zostały przeniesione w wyniku edycji.</span><span class="sxs-lookup"><span data-stu-id="4dfa3-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dfa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dfa3-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="4dfa3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4dfa3-105">Members</span></span>  
  
|<span data-ttu-id="4dfa3-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4dfa3-106">Member</span></span>|<span data-ttu-id="4dfa3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4dfa3-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="4dfa3-108">Token metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="4dfa3-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="4dfa3-109">Liczba wierszy, które zostały przeniesione przez metodę.</span><span class="sxs-lookup"><span data-stu-id="4dfa3-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4dfa3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dfa3-110">Requirements</span></span>  
 <span data-ttu-id="4dfa3-111">**Nagłówek:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="4dfa3-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfa3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dfa3-112">See also</span></span>

- [<span data-ttu-id="4dfa3-113">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="4dfa3-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
