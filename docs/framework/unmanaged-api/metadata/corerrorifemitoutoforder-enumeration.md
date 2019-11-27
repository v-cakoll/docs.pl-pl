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
ms.openlocfilehash: 57460ba30a8ce974b5ca89f76796c4dcf49ffecf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443587"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="2339f-102">CorErrorIfEmitOutOfOrder — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2339f-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="2339f-103">Zawiera wartości flag, które wskazują warunki, w których komunikat o błędzie powinien zostać wygenerowany, gdy metadane są emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2339f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2339f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2339f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2339f-105">Members</span></span>  
  
|<span data-ttu-id="2339f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2339f-106">Member</span></span>|<span data-ttu-id="2339f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2339f-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="2339f-108">Wskazuje zachowanie domyślne, które nie generuje komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="2339f-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="2339f-109">Wskazuje, że kompilator nie powinien generować komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="2339f-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="2339f-110">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy pole, właściwość, zdarzenie, metoda lub parametr są emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="2339f-111">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="2339f-112">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy pole jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="2339f-113">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy parametr jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="2339f-114">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="2339f-115">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowane poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="2339f-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2339f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2339f-116">Requirements</span></span>  
 <span data-ttu-id="2339f-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2339f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2339f-118">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="2339f-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2339f-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2339f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2339f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2339f-120">See also</span></span>

- [<span data-ttu-id="2339f-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="2339f-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
