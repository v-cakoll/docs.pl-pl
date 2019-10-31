---
title: DELETE — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja DELETE Usuwa określoną właściwość i wszystkie jej kwalifikatory z definicji klasy CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127666"
---
# <a name="delete-function"></a><span data-ttu-id="6b8f4-103">Delete, funkcja</span><span class="sxs-lookup"><span data-stu-id="6b8f4-103">Delete function</span></span>

<span data-ttu-id="6b8f4-104">Usuwa określoną właściwość i wszystkie jej kwalifikatory z definicji klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6b8f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b8f4-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="6b8f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b8f4-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="6b8f4-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="6b8f4-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="6b8f4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="6b8f4-109">podczas Nazwa właściwości do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="6b8f4-110">`wszName` musi być wskaźnikiem do prawidłowej `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b8f4-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b8f4-111">Return value</span></span>

<span data-ttu-id="6b8f4-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6b8f4-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6b8f4-113">Stała</span><span class="sxs-lookup"><span data-stu-id="6b8f4-113">Constant</span></span>  |<span data-ttu-id="6b8f4-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="6b8f4-114">Value</span></span>  |<span data-ttu-id="6b8f4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6b8f4-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="6b8f4-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6b8f4-116">0x80041001</span></span> | <span data-ttu-id="6b8f4-117">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="6b8f4-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="6b8f4-118">0x80041016</span></span> | <span data-ttu-id="6b8f4-119">Nie można usunąć właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6b8f4-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6b8f4-120">0x80041008</span></span> | <span data-ttu-id="6b8f4-121">`wszName` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="6b8f4-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6b8f4-122">0x80041002</span></span> | <span data-ttu-id="6b8f4-123">Określona właściwość nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6b8f4-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6b8f4-124">0x80041006</span></span> | <span data-ttu-id="6b8f4-125">Za mało pamięci, aby ukończyć operację.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="6b8f4-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="6b8f4-126">0x8004101c</span></span> | <span data-ttu-id="6b8f4-127">Właściwość jest dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="6b8f4-128">Właściwość jest właściwością systemową.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6b8f4-129">0</span><span class="sxs-lookup"><span data-stu-id="6b8f4-129">0</span></span> | <span data-ttu-id="6b8f4-130">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="6b8f4-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="6b8f4-131">0x80041030</span></span> | <span data-ttu-id="6b8f4-132">Funkcja usunęła wartość domyślną przesłonięcia dla bieżącej klasy.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="6b8f4-133">Wartość domyślna tej właściwości w klasie nadrzędnej została ponownie aktywowana.</span><span class="sxs-lookup"><span data-stu-id="6b8f4-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6b8f4-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b8f4-134">Remarks</span></span>

<span data-ttu-id="6b8f4-135">Ta funkcja otacza wywołanie metody [IWbemClassObject::D Usuń](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .</span><span class="sxs-lookup"><span data-stu-id="6b8f4-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6b8f4-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b8f4-136">Requirements</span></span>

<span data-ttu-id="6b8f4-137">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b8f4-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6b8f4-138">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="6b8f4-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6b8f4-139">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6b8f4-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6b8f4-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b8f4-140">See also</span></span>

- [<span data-ttu-id="6b8f4-141">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="6b8f4-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
