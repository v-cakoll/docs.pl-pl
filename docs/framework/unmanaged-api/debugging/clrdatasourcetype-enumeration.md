---
title: CLRDataSourceType, Wyliczenie
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
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274096"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="c4f6e-102">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c4f6e-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="c4f6e-103">Dostarcza wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="c4f6e-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c4f6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4f6e-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="c4f6e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c4f6e-105">Members</span></span>

| <span data-ttu-id="c4f6e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c4f6e-106">Member</span></span>                        | <span data-ttu-id="c4f6e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c4f6e-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="c4f6e-108">Aby wskazać, że nic nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c4f6e-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="c4f6e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4f6e-109">Remarks</span></span>

<span data-ttu-id="c4f6e-110">To wyliczenie jest przechowywane wewnątrz środowiska uruchomieniowego i nie jest ujawniane za pomocą żadnych nagłówków ani plików bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c4f6e-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c4f6e-111">Aby go użyć, zdefiniuj Wyliczenie zgodnie z definicją powyżej w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c4f6e-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="c4f6e-112">Jest to również alias `CLRDATA_ENUM` , tak jak wspomniano w przypadku [wspólnych typów danych](../common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="c4f6e-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c4f6e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4f6e-113">Requirements</span></span>

<span data-ttu-id="c4f6e-114">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4f6e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c4f6e-115">**Nagłówki** Brak</span><span class="sxs-lookup"><span data-stu-id="c4f6e-115">**Header:** None</span></span>  
<span data-ttu-id="c4f6e-116">**Biblioteki** Brak</span><span class="sxs-lookup"><span data-stu-id="c4f6e-116">**Library:** None</span></span>  
<span data-ttu-id="c4f6e-117">**.NET Framework wersje:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c4f6e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c4f6e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4f6e-118">See also</span></span>

- [<span data-ttu-id="c4f6e-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c4f6e-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="c4f6e-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c4f6e-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
