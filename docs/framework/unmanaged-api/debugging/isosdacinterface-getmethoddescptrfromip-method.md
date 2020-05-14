---
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP, Metoda'
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
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396930"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="f8338-102">ISOSDacInterface:: GetMethodDescPtrFromIP, Metoda</span><span class="sxs-lookup"><span data-stu-id="f8338-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="f8338-103">Pobiera wskaźnik MethodDesc odpowiadającego metodzie zawierającej podanego adresu instrukcji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="f8338-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f8338-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8338-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="f8338-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8338-105">Parameters</span></span>

`ip`\
<span data-ttu-id="f8338-106">podczas Adres w ramach metody w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8338-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="f8338-107">określoną Adres `MethodDesc` dla określonej metody.</span><span class="sxs-lookup"><span data-stu-id="f8338-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8338-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8338-108">Remarks</span></span>

<span data-ttu-id="f8338-109">Podana metoda jest częścią [ `ISOSDacInterface` interfejsu](isosdacinterface-interface.md) i odnosi się do 22 gniazda tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="f8338-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8338-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8338-110">Requirements</span></span>

<span data-ttu-id="f8338-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8338-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f8338-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="f8338-112">**Header:** None</span></span>  
<span data-ttu-id="f8338-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="f8338-113">**Library:** None</span></span>  
<span data-ttu-id="f8338-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8338-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f8338-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8338-115">See also</span></span>

- [<span data-ttu-id="f8338-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f8338-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="f8338-117">ISOSDacInterface, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8338-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
