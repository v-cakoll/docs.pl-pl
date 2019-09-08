---
title: CloneEnumWbemClassObject — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CloneEnumWbemClassObject wykonuje logiczną kopię modułu wyliczającego.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605314f94fd82d2a2cd7be105dde9e273f607bc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798697"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="0df1a-103">CloneEnumWbemClassObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="0df1a-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="0df1a-104">Tworzy logiczną kopię modułu wyliczającego, zachowując jego bieżącą pozycję w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="0df1a-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0df1a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0df1a-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a><span data-ttu-id="0df1a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0df1a-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="0df1a-107">określoną Odbiera wskaźnik do nowego [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="0df1a-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="0df1a-108">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0df1a-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="0df1a-109">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="0df1a-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="0df1a-110">określoną Wskaźnik do wystąpienia [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) , który ma zostać sklonowany.</span><span class="sxs-lookup"><span data-stu-id="0df1a-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="0df1a-111">podczas Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0df1a-111">[in] The user name.</span></span> <span data-ttu-id="0df1a-112">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0df1a-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="0df1a-113">podczas Hasło.</span><span class="sxs-lookup"><span data-stu-id="0df1a-113">[in] The password.</span></span> <span data-ttu-id="0df1a-114">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0df1a-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="0df1a-115">`strAuthority`\ [in] nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0df1a-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="0df1a-116">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0df1a-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0df1a-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0df1a-117">Return value</span></span>

<span data-ttu-id="0df1a-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="0df1a-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0df1a-119">Stała</span><span class="sxs-lookup"><span data-stu-id="0df1a-119">Constant</span></span>  |<span data-ttu-id="0df1a-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="0df1a-120">Value</span></span>  |<span data-ttu-id="0df1a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0df1a-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="0df1a-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0df1a-122">0x80041001</span></span> | <span data-ttu-id="0df1a-123">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="0df1a-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0df1a-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0df1a-124">0x80041008</span></span> | <span data-ttu-id="0df1a-125">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="0df1a-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0df1a-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0df1a-126">0x80041006</span></span> | <span data-ttu-id="0df1a-127">Za mało dostępnej pamięci, aby ukończyć operację.</span><span class="sxs-lookup"><span data-stu-id="0df1a-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="0df1a-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="0df1a-128">0x80041015</span></span> | <span data-ttu-id="0df1a-129">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0df1a-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0df1a-130">0</span><span class="sxs-lookup"><span data-stu-id="0df1a-130">0</span></span> | <span data-ttu-id="0df1a-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0df1a-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="0df1a-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0df1a-132">Remarks</span></span>

<span data-ttu-id="0df1a-133">Ta funkcja otacza wywołanie metody [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="0df1a-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="0df1a-134">Ta metoda zapewnia tylko kopię "najlepszej pracy".</span><span class="sxs-lookup"><span data-stu-id="0df1a-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="0df1a-135">Ze względu na dynamiczny charakter wielu obiektów CIM, istnieje możliwość, że nowy moduł wyliczający nie wylicza tego samego zestawu obiektów, co źródłowy moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="0df1a-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="0df1a-136">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="0df1a-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="0df1a-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="0df1a-137">Example</span></span>

<span data-ttu-id="0df1a-138">Aby zapoznać się z przykładem, zobacz metodę [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="0df1a-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0df1a-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0df1a-139">Requirements</span></span>
 <span data-ttu-id="0df1a-140">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df1a-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="0df1a-141">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0df1a-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="0df1a-142">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0df1a-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0df1a-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0df1a-143">See also</span></span>

- [<span data-ttu-id="0df1a-144">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="0df1a-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
