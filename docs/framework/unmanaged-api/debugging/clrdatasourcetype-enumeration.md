---
title: Wyliczenie CLRDataSourceType
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c8b3f338659e2784db8deca3e1776e7926c30c32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506087"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="49e07-102">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="49e07-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="49e07-103">Zawiera wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="49e07-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="49e07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49e07-104">Syntax</span></span>

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="49e07-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="49e07-105">Members</span></span>

| <span data-ttu-id="49e07-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="49e07-106">Member</span></span>                        | <span data-ttu-id="49e07-107">Opis</span><span class="sxs-lookup"><span data-stu-id="49e07-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="49e07-108">Aby wskazać, że nic ma zastosowanie</span><span class="sxs-lookup"><span data-stu-id="49e07-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="49e07-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49e07-109">Remarks</span></span>

<span data-ttu-id="49e07-110">To wyliczenie znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="49e07-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="49e07-111">Aby go użyć, należy zdefiniować wyliczenie zgodnie z definicją w kodzie.</span><span class="sxs-lookup"><span data-stu-id="49e07-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="49e07-112">Dotyczy to również alias do `CLRDATA_ENUM` zgodnie z opisem w [standardowe typy danych](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="49e07-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="49e07-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49e07-113">Requirements</span></span>

<span data-ttu-id="49e07-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49e07-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="49e07-115">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="49e07-115">**Header:** None</span></span>  
<span data-ttu-id="49e07-116">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="49e07-116">**Library:** None</span></span>  
<span data-ttu-id="49e07-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="49e07-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="49e07-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49e07-118">See also</span></span>

- [<span data-ttu-id="49e07-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="49e07-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="49e07-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="49e07-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
