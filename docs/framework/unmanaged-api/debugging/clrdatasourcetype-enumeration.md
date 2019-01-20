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
ms.openlocfilehash: 36651de5053e994103f79c9021e8e18e126f91fa
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416099"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="31bab-102">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="31bab-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="31bab-103">Zawiera wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="31bab-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="31bab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31bab-104">Syntax</span></span>

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="31bab-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="31bab-105">Members</span></span>

| <span data-ttu-id="31bab-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="31bab-106">Member</span></span>                        | <span data-ttu-id="31bab-107">Opis</span><span class="sxs-lookup"><span data-stu-id="31bab-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="31bab-108">Aby wskazać, że nic ma zastosowanie</span><span class="sxs-lookup"><span data-stu-id="31bab-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="31bab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31bab-109">Remarks</span></span>

<span data-ttu-id="31bab-110">To wyliczenie znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="31bab-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="31bab-111">Aby go użyć, należy zdefiniować wyliczenie zgodnie z definicją w kodzie.</span><span class="sxs-lookup"><span data-stu-id="31bab-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="31bab-112">Dotyczy to również alias do `CLRDATA_ENUM` zgodnie z opisem w [standardowe typy danych](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="31bab-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="31bab-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31bab-113">Requirements</span></span>

<span data-ttu-id="31bab-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31bab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="31bab-115">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="31bab-115">**Header:** None</span></span>  
<span data-ttu-id="31bab-116">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="31bab-116">**Library:** None</span></span>  
<span data-ttu-id="31bab-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="31bab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="31bab-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31bab-118">See Also</span></span>

- [<span data-ttu-id="31bab-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="31bab-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="31bab-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="31bab-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
