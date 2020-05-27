---
title: CorErrorIfEmitOutOfOrder — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007440"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="d372a-102">CorErrorIfEmitOutOfOrder — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d372a-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="d372a-103">Zawiera wartości flag, które wskazują warunki, w których komunikat o błędzie powinien zostać wygenerowany, gdy metadane są emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d372a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d372a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="d372a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d372a-105">Members</span></span>  
  
|<span data-ttu-id="d372a-106">Członek</span><span class="sxs-lookup"><span data-stu-id="d372a-106">Member</span></span>|<span data-ttu-id="d372a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d372a-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="d372a-108">Wskazuje zachowanie domyślne, które nie generuje komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="d372a-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="d372a-109">Wskazuje, że kompilator nie powinien generować komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="d372a-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="d372a-110">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy pole, właściwość, zdarzenie, metoda lub parametr są emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="d372a-111">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="d372a-112">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy pole jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="d372a-113">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy parametr jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="d372a-114">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="d372a-115">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="d372a-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d372a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d372a-116">Requirements</span></span>  
 <span data-ttu-id="d372a-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d372a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d372a-118">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d372a-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d372a-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d372a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d372a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d372a-120">See also</span></span>

- [<span data-ttu-id="d372a-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d372a-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
