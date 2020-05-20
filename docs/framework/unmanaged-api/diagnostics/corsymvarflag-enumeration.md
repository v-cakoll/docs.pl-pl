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
ms.openlocfilehash: d41e048b67d4bc7159f6dd5266457651f1658290
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420594"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="077ec-102">CorSymVarFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="077ec-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="077ec-103">Wskazuje, czy zmienna jest generowana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="077ec-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="077ec-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="077ec-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="077ec-105">Members</span></span>  
  
|<span data-ttu-id="077ec-106">Członek</span><span class="sxs-lookup"><span data-stu-id="077ec-106">Member</span></span>|<span data-ttu-id="077ec-107">Opis</span><span class="sxs-lookup"><span data-stu-id="077ec-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="077ec-108">Wskazuje, że dana zmienna jest generowana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="077ec-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="077ec-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="077ec-109">Requirements</span></span>  
 <span data-ttu-id="077ec-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="077ec-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077ec-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="077ec-111">See also</span></span>

- [<span data-ttu-id="077ec-112">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="077ec-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
