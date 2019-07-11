---
title: Funkcja CloneEnumWbemClassObject (niezarządzany wykaz interfejsów API)
description: Funkcja CloneEnumWbemClassObject sprawia, że logicznej kopii modułu wyliczającego.
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
ms.openlocfilehash: ab660769a49cf12b129cb7f44b8378053a231f8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761628"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="8603b-103">CloneEnumWbemClassObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="8603b-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="8603b-104">Tworzy kopię logiczne moduł wyliczający, zachowując jego bieżącej pozycji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="8603b-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8603b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8603b-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="8603b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8603b-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="8603b-107">[out] Otrzymuje wskaźnik do nowego [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="8603b-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="8603b-108">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="8603b-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="8603b-109">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="8603b-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="8603b-110">[out] Wskaźnik do [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) wystąpienia można sklonować.</span><span class="sxs-lookup"><span data-stu-id="8603b-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="8603b-111">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8603b-111">[in] The user name.</span></span> <span data-ttu-id="8603b-112">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8603b-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="8603b-113">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="8603b-113">[in] The password.</span></span> <span data-ttu-id="8603b-114">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8603b-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="8603b-115">`strAuthority`\ [w] nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8603b-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="8603b-116">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8603b-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="8603b-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8603b-117">Return value</span></span>

<span data-ttu-id="8603b-118">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="8603b-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8603b-119">Stała</span><span class="sxs-lookup"><span data-stu-id="8603b-119">Constant</span></span>  |<span data-ttu-id="8603b-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="8603b-120">Value</span></span>  |<span data-ttu-id="8603b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8603b-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="8603b-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8603b-122">0x80041001</span></span> | <span data-ttu-id="8603b-123">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="8603b-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8603b-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8603b-124">0x80041008</span></span> | <span data-ttu-id="8603b-125">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8603b-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8603b-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8603b-126">0x80041006</span></span> | <span data-ttu-id="8603b-127">Nie ma wystarczającej ilości pamięci dostępnej ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="8603b-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="8603b-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="8603b-128">0x80041015</span></span> | <span data-ttu-id="8603b-129">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="8603b-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="8603b-130">0</span><span class="sxs-lookup"><span data-stu-id="8603b-130">0</span></span> | <span data-ttu-id="8603b-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8603b-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="8603b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8603b-132">Remarks</span></span>

<span data-ttu-id="8603b-133">Ta funkcja zawija wywołanie do [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="8603b-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="8603b-134">Ta metoda tworzy wyłącznie kopię "starań".</span><span class="sxs-lookup"><span data-stu-id="8603b-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="8603b-135">Ze względu na dynamiczny charakter wiele obiektów modelu wspólnych informacji jest możliwe, że nowy moduł wyliczający nie wylicza ten sam zestaw obiektów jako modułu wyliczającego źródła.</span><span class="sxs-lookup"><span data-stu-id="8603b-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="8603b-136">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="8603b-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="8603b-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="8603b-137">Example</span></span>

<span data-ttu-id="8603b-138">Aby uzyskać przykład, zobacz [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="8603b-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8603b-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8603b-139">Requirements</span></span>
 <span data-ttu-id="8603b-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8603b-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="8603b-141">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8603b-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="8603b-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8603b-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8603b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8603b-143">See also</span></span>

- [<span data-ttu-id="8603b-144">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="8603b-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
