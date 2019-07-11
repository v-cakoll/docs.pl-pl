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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16f6d7bf6fa1730d50cfe81526817e492a453dad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781987"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="ddcb8-102">CorErrorIfEmitOutOfOrder — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ddcb8-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="ddcb8-103">Zawiera wartości flagi, które określają warunki, w których mają być generowane metadanych jest emitowane poza kolejnością komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddcb8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ddcb8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ddcb8-105">Members</span></span>  
  
|<span data-ttu-id="ddcb8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ddcb8-106">Member</span></span>|<span data-ttu-id="ddcb8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ddcb8-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="ddcb8-108">Wskazuje zachowanie domyślne, które generują komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="ddcb8-109">Wskazuje, że kompilator nie powinna generować komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="ddcb8-110">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy pola, właściwości, zdarzenia, metody lub parametru jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="ddcb8-111">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="ddcb8-112">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy pole jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="ddcb8-113">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy parametr jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="ddcb8-114">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="ddcb8-115">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ddcb8-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ddcb8-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddcb8-116">Requirements</span></span>  
 <span data-ttu-id="ddcb8-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcb8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcb8-118">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ddcb8-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ddcb8-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcb8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcb8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcb8-120">See also</span></span>

- [<span data-ttu-id="ddcb8-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ddcb8-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
