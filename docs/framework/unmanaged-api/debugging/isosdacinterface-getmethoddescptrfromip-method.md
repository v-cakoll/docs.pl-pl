---
title: Metoda ISOSDacInterface::GetMethodDescPtrFromIP
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c92b112262aa2bede03bddc1396947b5fdfd6286
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629987"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="2b2fe-102">Metoda ISOSDacInterface::GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="2b2fe-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="2b2fe-103">Pobiera wskaźnik MethodDesc odpowiadającej metody zawierającą adres instrukcji natywnych.</span><span class="sxs-lookup"><span data-stu-id="2b2fe-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2b2fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b2fe-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="2b2fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b2fe-105">Parameters</span></span>

`ip`\
<span data-ttu-id="2b2fe-106">[in] Adres w metodzie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b2fe-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="2b2fe-107">[out] Adres `MethodDesc` dla określonej metody.</span><span class="sxs-lookup"><span data-stu-id="2b2fe-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b2fe-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b2fe-108">Remarks</span></span>

<span data-ttu-id="2b2fe-109">Podana metoda jest częścią [ `ISOSDacInterface` interfejsu](isosdacinterface-interface.md) i odnosi się do 21 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="2b2fe-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b2fe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b2fe-110">Requirements</span></span>

<span data-ttu-id="2b2fe-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2fe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2b2fe-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="2b2fe-112">**Header:** None</span></span>  
<span data-ttu-id="2b2fe-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="2b2fe-113">**Library:** None</span></span>  
<span data-ttu-id="2b2fe-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2fe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2b2fe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b2fe-115">See also</span></span>

- [<span data-ttu-id="2b2fe-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2b2fe-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="2b2fe-117">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="2b2fe-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
