---
title: CreateClassEnumWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CreateClassEnumWmi zwraca moduł wyliczający dla wszystkich klas, które spełniają określone kryteria.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798741"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="d5a41-103">CreateClassEnumWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="d5a41-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="d5a41-104">Zwraca moduł wyliczający dla wszystkich klas, które spełniają określone kryteria wyboru.</span><span class="sxs-lookup"><span data-stu-id="d5a41-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d5a41-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5a41-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="d5a41-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5a41-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="d5a41-107">podczas Jeśli nie `null` lub puste, określa nazwę klasy nadrzędnej; moduł wyliczający zwraca tylko podklasy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="d5a41-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="d5a41-108">Jeśli jest to `null` lub puste i `lFlags` jest WBEM_FLAG_SHALLOW, zwraca tylko klasy najwyższego poziomu (klasy bez klasy nadrzędnej).</span><span class="sxs-lookup"><span data-stu-id="d5a41-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="d5a41-109">Jeśli jest lub `null` jest pusty i `lFlags` ma `WBEM_FLAG_DEEP`wartość, zwraca wszystkie klasy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5a41-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="d5a41-110">podczas Kombinacja flag mających wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5a41-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="d5a41-111">Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d5a41-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d5a41-112">Stała</span><span class="sxs-lookup"><span data-stu-id="d5a41-112">Constant</span></span>  |<span data-ttu-id="d5a41-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5a41-113">Value</span></span>  |<span data-ttu-id="d5a41-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d5a41-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="d5a41-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="d5a41-115">0x20000</span></span> | <span data-ttu-id="d5a41-116">W przypadku ustawienia funkcja pobiera zmienione kwalifikatory przechowywane w zlokalizowanej przestrzeni nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="d5a41-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="d5a41-117">Jeśli nie zostanie ustawiona, funkcja pobiera tylko kwalifikatory przechowywane w bezpośredniej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5a41-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="d5a41-118">0</span><span class="sxs-lookup"><span data-stu-id="d5a41-118">0</span></span> | <span data-ttu-id="d5a41-119">Wyliczenie obejmuje wszystkie podklasy w hierarchii, ale nie tę klasę.</span><span class="sxs-lookup"><span data-stu-id="d5a41-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="d5a41-120">1</span><span class="sxs-lookup"><span data-stu-id="d5a41-120">1</span></span> | <span data-ttu-id="d5a41-121">Wyliczenie obejmuje tylko czyste wystąpienia tej klasy i wyklucza wszystkie wystąpienia podklas, które nie znalazły właściwości w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="d5a41-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="d5a41-122">0x10</span><span class="sxs-lookup"><span data-stu-id="d5a41-122">0x10</span></span> | <span data-ttu-id="d5a41-123">Flaga powoduje wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d5a41-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="d5a41-124">0x20</span><span class="sxs-lookup"><span data-stu-id="d5a41-124">0x20</span></span> | <span data-ttu-id="d5a41-125">Funkcja zwraca moduł wyliczający tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="d5a41-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="d5a41-126">Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="d5a41-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="d5a41-127">0</span><span class="sxs-lookup"><span data-stu-id="d5a41-127">0</span></span> | <span data-ttu-id="d5a41-128">Usługa WMI zachowuje wskaźniki do obiektów w wyliczeniu do momentu ich zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="d5a41-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="d5a41-129">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` zapewniają najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="d5a41-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="d5a41-130">podczas Zazwyczaj ta wartość to `null`.</span><span class="sxs-lookup"><span data-stu-id="d5a41-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="d5a41-131">W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.</span><span class="sxs-lookup"><span data-stu-id="d5a41-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="d5a41-132">określoną Odbiera wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="d5a41-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="d5a41-133">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="d5a41-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="d5a41-134">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="d5a41-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="d5a41-135">podczas Wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , który reprezentuje bieżącą przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d5a41-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="d5a41-136">podczas Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d5a41-136">[in] The user name.</span></span> <span data-ttu-id="d5a41-137">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d5a41-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="d5a41-138">podczas Hasło.</span><span class="sxs-lookup"><span data-stu-id="d5a41-138">[in] The password.</span></span> <span data-ttu-id="d5a41-139">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d5a41-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="d5a41-140">podczas Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d5a41-140">[in] The domain name of the user.</span></span> <span data-ttu-id="d5a41-141">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d5a41-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d5a41-142">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5a41-142">Return value</span></span>

<span data-ttu-id="d5a41-143">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d5a41-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d5a41-144">Stała</span><span class="sxs-lookup"><span data-stu-id="d5a41-144">Constant</span></span>  |<span data-ttu-id="d5a41-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5a41-145">Value</span></span>  |<span data-ttu-id="d5a41-146">Opis</span><span class="sxs-lookup"><span data-stu-id="d5a41-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="d5a41-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="d5a41-147">0x80041003</span></span> | <span data-ttu-id="d5a41-148">Użytkownik nie ma uprawnienia do wyświetlania jednej lub więcej klas, które funkcja może zwrócić.</span><span class="sxs-lookup"><span data-stu-id="d5a41-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="d5a41-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d5a41-149">0x80041001</span></span> | <span data-ttu-id="d5a41-150">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="d5a41-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="d5a41-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="d5a41-151">0x80041010</span></span> | <span data-ttu-id="d5a41-152">`strSuperClass`nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="d5a41-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d5a41-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d5a41-153">0x80041008</span></span> | <span data-ttu-id="d5a41-154">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d5a41-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d5a41-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d5a41-155">0x80041006</span></span> | <span data-ttu-id="d5a41-156">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="d5a41-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="d5a41-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="d5a41-157">0x80041033</span></span> | <span data-ttu-id="d5a41-158">Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="d5a41-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="d5a41-159">Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="d5a41-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="d5a41-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="d5a41-160">0x80041015</span></span> | <span data-ttu-id="d5a41-161">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d5a41-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d5a41-162">0</span><span class="sxs-lookup"><span data-stu-id="d5a41-162">0</span></span> | <span data-ttu-id="d5a41-163">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d5a41-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="d5a41-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5a41-164">Remarks</span></span>

<span data-ttu-id="d5a41-165">Ta funkcja otacza wywołanie metody [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .</span><span class="sxs-lookup"><span data-stu-id="d5a41-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="d5a41-166">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="d5a41-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5a41-167">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5a41-167">Requirements</span></span>

<span data-ttu-id="d5a41-168">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a41-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d5a41-169">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d5a41-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="d5a41-170">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a41-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d5a41-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5a41-171">See also</span></span>

- [<span data-ttu-id="d5a41-172">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d5a41-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
