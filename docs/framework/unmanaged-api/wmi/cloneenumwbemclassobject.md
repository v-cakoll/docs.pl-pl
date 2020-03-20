---
title: CloneEnumWbemClassObject, funkcja (niezarządzane odwołanie do interfejsu API)
description: CloneEnumWbemClassObject funkcja sprawia, że logiczna kopia modułu wyliczacza.
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
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175021"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="bb83d-103">CloneEnumWbemClassObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="bb83d-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="bb83d-104">Tworzy logiczną kopię modułu wyliczającego, zachowując jego bieżącą pozycję w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="bb83d-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bb83d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb83d-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="bb83d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb83d-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="bb83d-107">[na zewnątrz] Odbiera wskaźnik do nowego [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="bb83d-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="bb83d-108">[w] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="bb83d-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="bb83d-109">[w] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="bb83d-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="bb83d-110">[na zewnątrz] Wskaźnik do [wystąpienia IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) do sklonowania.</span><span class="sxs-lookup"><span data-stu-id="bb83d-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="bb83d-111">[w] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb83d-111">[in] The user name.</span></span> <span data-ttu-id="bb83d-112">Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="bb83d-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="bb83d-113">[w] Hasło.</span><span class="sxs-lookup"><span data-stu-id="bb83d-113">[in] The password.</span></span> <span data-ttu-id="bb83d-114">Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="bb83d-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="bb83d-115">[w] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb83d-115">[in] The domain name of the user.</span></span> <span data-ttu-id="bb83d-116">Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="bb83d-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb83d-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb83d-117">Return value</span></span>

<span data-ttu-id="bb83d-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bb83d-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bb83d-119">Stały</span><span class="sxs-lookup"><span data-stu-id="bb83d-119">Constant</span></span>  |<span data-ttu-id="bb83d-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="bb83d-120">Value</span></span>  |<span data-ttu-id="bb83d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="bb83d-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="bb83d-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bb83d-122">0x80041001</span></span> | <span data-ttu-id="bb83d-123">Wystąpiła ogólna porażka.</span><span class="sxs-lookup"><span data-stu-id="bb83d-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bb83d-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bb83d-124">0x80041008</span></span> | <span data-ttu-id="bb83d-125">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="bb83d-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bb83d-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bb83d-126">0x80041006</span></span> | <span data-ttu-id="bb83d-127">Za mało pamięci jest dostępna zakończyć operację.</span><span class="sxs-lookup"><span data-stu-id="bb83d-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="bb83d-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="bb83d-128">0x80041015</span></span> | <span data-ttu-id="bb83d-129">Połączenie procedury zdalnej (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="bb83d-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bb83d-130">0</span><span class="sxs-lookup"><span data-stu-id="bb83d-130">0</span></span> | <span data-ttu-id="bb83d-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bb83d-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bb83d-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb83d-132">Remarks</span></span>

<span data-ttu-id="bb83d-133">Ta funkcja zawija wywołanie [metody IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="bb83d-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="bb83d-134">Ta metoda sprawia, że tylko "najlepszy wysiłek" kopię.</span><span class="sxs-lookup"><span data-stu-id="bb83d-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="bb83d-135">Ze względu na dynamiczny charakter wielu obiektów CIM jest możliwe, że nowy wyliczacz nie wylicza ten sam zestaw obiektów jako wyliczacz źródłowy.</span><span class="sxs-lookup"><span data-stu-id="bb83d-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="bb83d-136">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="bb83d-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="bb83d-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb83d-137">Example</span></span>

<span data-ttu-id="bb83d-138">Na przykład zobacz [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="bb83d-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb83d-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb83d-139">Requirements</span></span>
 <span data-ttu-id="bb83d-140">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb83d-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bb83d-141">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bb83d-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="bb83d-142">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bb83d-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bb83d-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb83d-143">See also</span></span>

- [<span data-ttu-id="bb83d-144">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="bb83d-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
