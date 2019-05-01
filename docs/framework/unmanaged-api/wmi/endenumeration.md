---
title: Funkcja EndEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja EndEnumeration kończy wyliczenia.
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65904da9efea90d31960d71ae0da8c81dffeccf1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000470"
---
# <a name="endenumeration-function"></a><span data-ttu-id="60f21-103">EndEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="60f21-103">EndEnumeration function</span></span>

<span data-ttu-id="60f21-104">Kończy sekwencji wyliczenie pracę z wywołaniem [funkcja Beingenumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="60f21-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="60f21-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="60f21-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="60f21-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="60f21-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="60f21-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="60f21-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="60f21-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60f21-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="60f21-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60f21-109">Return value</span></span>

<span data-ttu-id="60f21-110">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="60f21-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="60f21-111">Stała</span><span class="sxs-lookup"><span data-stu-id="60f21-111">Constant</span></span>  |<span data-ttu-id="60f21-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="60f21-112">Value</span></span>  |<span data-ttu-id="60f21-113">Opis</span><span class="sxs-lookup"><span data-stu-id="60f21-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="60f21-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="60f21-114">0x80041001</span></span> | <span data-ttu-id="60f21-115">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="60f21-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="60f21-116">0</span><span class="sxs-lookup"><span data-stu-id="60f21-116">0</span></span> | <span data-ttu-id="60f21-117">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="60f21-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="60f21-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60f21-118">Remarks</span></span>

<span data-ttu-id="60f21-119">Ta funkcja zawija wywołanie do [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.</span><span class="sxs-lookup"><span data-stu-id="60f21-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="60f21-120">Wywołanie `EndEnumeration` funkcja nie jest wymagana, ale jest zalecane, ponieważ zwalnia zasoby skojarzone z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="60f21-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="60f21-121">Jednak zasoby są dealokowane automatycznie po uruchomieniu dalej wyliczenie lub obiektu jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="60f21-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="60f21-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60f21-122">Requirements</span></span>

<span data-ttu-id="60f21-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f21-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="60f21-124">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="60f21-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="60f21-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60f21-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="60f21-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60f21-126">See also</span></span>

- [<span data-ttu-id="60f21-127">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="60f21-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)