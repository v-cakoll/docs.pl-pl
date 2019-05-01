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
ms.openlocfilehash: adef1010d08561c0a0fe38480fe0d2f519a80b49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993437"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="29044-102">CorSymAddrKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="29044-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="29044-103">Wskazuje typ adresu pamięci.</span><span class="sxs-lookup"><span data-stu-id="29044-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29044-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29044-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="29044-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="29044-105">Members</span></span>  
  
|<span data-ttu-id="29044-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="29044-106">Member</span></span>|<span data-ttu-id="29044-107">Opis</span><span class="sxs-lookup"><span data-stu-id="29044-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="29044-108">Wskazuje Microsoft intermediate language (MSIL) lokalnej zmiennej lub parametru indeksu.</span><span class="sxs-lookup"><span data-stu-id="29044-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="29044-109">Oznacza względny adres wirtualny do modułu.</span><span class="sxs-lookup"><span data-stu-id="29044-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="29044-110">Wskazuje rejestru procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="29044-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="29044-111">Wskazuje, czy pierwszy adres jest rejestru, a drugi adres jest przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="29044-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="29044-112">Określa przesunięcie od adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="29044-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="29044-113">Wskazuje, że pierwszy adres jest niski część rejestr i drugi adres jest wysokiej część.</span><span class="sxs-lookup"><span data-stu-id="29044-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="29044-114">Wskazuje, że pierwszy adres jest niski część rejestr, druga jest wysokiej część i trzeci to przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="29044-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="29044-115">Wskazuje, że pierwszy adres jest rejestr, drugą jest wartość przesunięcia i trzeci jest wysoka części rejestru.</span><span class="sxs-lookup"><span data-stu-id="29044-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="29044-116">Wskazuje, czy pierwszy adres jest początku pola, a drugi adres jest długość pola.</span><span class="sxs-lookup"><span data-stu-id="29044-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="29044-117">Wskazuje, czy pierwszy adres jest sekcji, a drugi adres jest przesunięta.</span><span class="sxs-lookup"><span data-stu-id="29044-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29044-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29044-118">Requirements</span></span>  
 <span data-ttu-id="29044-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29044-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29044-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29044-120">See also</span></span>

- [<span data-ttu-id="29044-121">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="29044-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
