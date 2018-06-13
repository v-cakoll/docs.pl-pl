---
title: CorSymAddrKind — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98cf49714829b4b2f80e0240c2ebde7fa6c280e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425408"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="8722e-102">CorSymAddrKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8722e-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="8722e-103">Wskazuje typ adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="8722e-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8722e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8722e-104">Syntax</span></span>  
  
```  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="8722e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8722e-105">Members</span></span>  
  
|<span data-ttu-id="8722e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8722e-106">Member</span></span>|<span data-ttu-id="8722e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8722e-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="8722e-108">Wskazuje Microsoft język pośredni (MSIL) lokalnej zmiennej lub parametru indeks.</span><span class="sxs-lookup"><span data-stu-id="8722e-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="8722e-109">Wskazuje wirtualny adres względny w module.</span><span class="sxs-lookup"><span data-stu-id="8722e-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="8722e-110">Wskazuje rejestru procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="8722e-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="8722e-111">Wskazuje, że pierwszy adres jest rejestr i drugi adres jest przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="8722e-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="8722e-112">Określa przesunięcie od adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="8722e-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="8722e-113">Wskazuje, że pierwszy adres jest niski część rejestru i drugi adres jest wysoki.</span><span class="sxs-lookup"><span data-stu-id="8722e-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="8722e-114">Wskazuje, że pierwszy adres jest niski część rejestr, drugi ma wysoką części i trzeci jest przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="8722e-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="8722e-115">Wskazuje, że rejestr jest pierwszym adresem, przesunięcie jest drugi i trzeci jest wysoka części rejestru.</span><span class="sxs-lookup"><span data-stu-id="8722e-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="8722e-116">Wskazuje, że pierwszy adres jest początek pola i drugi adres jest długość pola.</span><span class="sxs-lookup"><span data-stu-id="8722e-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="8722e-117">Wskazuje, że sekcja jest pierwszym adresem i drugi adres jest przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="8722e-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8722e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8722e-118">Requirements</span></span>  
 <span data-ttu-id="8722e-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8722e-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8722e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8722e-120">See Also</span></span>  
 [<span data-ttu-id="8722e-121">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="8722e-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
