---
title: Funkcja CreateClassEnumWmi (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: 0a4d2c2bd28640d0ac7124f8e0864e9e72fb1eb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935632"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="03b76-103">CreateClassEnumWmi — funkcja</span><span class="sxs-lookup"><span data-stu-id="03b76-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="03b76-104">Zwraca moduł wyliczający dla wszystkich klas, które spełniają kryteria określonego zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="03b76-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="03b76-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03b76-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="03b76-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03b76-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="03b76-107">[in] W przeciwnym razie `null` lub puste, określa nazwę klasy nadrzędnej; moduł wyliczający zwraca tylko podklasy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="03b76-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="03b76-108">Jeśli jest `null` lub puste i `lFlags` WBEM_FLAG_SHALLOW, zwraca tylko klas najwyższego poziomu (klas z nie klasy nadrzędnej).</span><span class="sxs-lookup"><span data-stu-id="03b76-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="03b76-109">Jeśli jest `null` lub puste i `lFlags` jest `WBEM_FLAG_DEEP`, zwraca wszystkie klasy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="03b76-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="03b76-110">[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="03b76-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="03b76-111">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="03b76-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="03b76-112">Stała</span><span class="sxs-lookup"><span data-stu-id="03b76-112">Constant</span></span>  |<span data-ttu-id="03b76-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="03b76-113">Value</span></span>  |<span data-ttu-id="03b76-114">Opis</span><span class="sxs-lookup"><span data-stu-id="03b76-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="03b76-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="03b76-115">0x20000</span></span> | <span data-ttu-id="03b76-116">Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów, przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="03b76-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="03b76-117">W przeciwnym razie zestawu, funkcja pobiera kwalifikatory przechowywanych w bezpośrednim przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="03b76-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="03b76-118">0</span><span class="sxs-lookup"><span data-stu-id="03b76-118">0</span></span> | <span data-ttu-id="03b76-119">Wyliczenie zawiera podklasami w hierarchii, ale nie tej klasy.</span><span class="sxs-lookup"><span data-stu-id="03b76-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="03b76-120">1</span><span class="sxs-lookup"><span data-stu-id="03b76-120">1</span></span> | <span data-ttu-id="03b76-121">Wyliczenie zawiera tylko czyste wystąpienia tej klasy i nie obejmuje wszystkich wystąpień podklas, które dostarczają właściwości nie można odnaleźć w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="03b76-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="03b76-122">0x10</span><span class="sxs-lookup"><span data-stu-id="03b76-122">0x10</span></span> | <span data-ttu-id="03b76-123">Flaga powoduje, że wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="03b76-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="03b76-124">0x20</span><span class="sxs-lookup"><span data-stu-id="03b76-124">0x20</span></span> | <span data-ttu-id="03b76-125">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="03b76-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="03b76-126">Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="03b76-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="03b76-127">0</span><span class="sxs-lookup"><span data-stu-id="03b76-127">0</span></span> | <span data-ttu-id="03b76-128">WMI zachowuje wskaźników do obiektów w wyliczeniu, dopóki ich wydaniu.</span><span class="sxs-lookup"><span data-stu-id="03b76-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="03b76-129">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` uzyskać najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="03b76-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="03b76-130">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="03b76-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="03b76-131">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="03b76-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="03b76-132">[out] Otrzymuje wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="03b76-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="03b76-133">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="03b76-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="03b76-134">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="03b76-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="03b76-135">[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="03b76-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="03b76-136">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03b76-136">[in] The user name.</span></span> <span data-ttu-id="03b76-137">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="03b76-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="03b76-138">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="03b76-138">[in] The password.</span></span> <span data-ttu-id="03b76-139">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="03b76-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="03b76-140">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03b76-140">[in] The domain name of the user.</span></span> <span data-ttu-id="03b76-141">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="03b76-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="03b76-142">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03b76-142">Return value</span></span>

<span data-ttu-id="03b76-143">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="03b76-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="03b76-144">Stała</span><span class="sxs-lookup"><span data-stu-id="03b76-144">Constant</span></span>  |<span data-ttu-id="03b76-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="03b76-145">Value</span></span>  |<span data-ttu-id="03b76-146">Opis</span><span class="sxs-lookup"><span data-stu-id="03b76-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="03b76-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="03b76-147">0x80041003</span></span> | <span data-ttu-id="03b76-148">Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji.</span><span class="sxs-lookup"><span data-stu-id="03b76-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="03b76-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="03b76-149">0x80041001</span></span> | <span data-ttu-id="03b76-150">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="03b76-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="03b76-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="03b76-151">0x80041010</span></span> | <span data-ttu-id="03b76-152">`strSuperClass` nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="03b76-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="03b76-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="03b76-153">0x80041008</span></span> | <span data-ttu-id="03b76-154">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="03b76-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="03b76-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="03b76-155">0x80041006</span></span> | <span data-ttu-id="03b76-156">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="03b76-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="03b76-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="03b76-157">0x80041033</span></span> | <span data-ttu-id="03b76-158">WMI został prawdopodobnie zatrzymane i ponowne uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="03b76-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="03b76-159">Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="03b76-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="03b76-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="03b76-160">0x80041015</span></span> | <span data-ttu-id="03b76-161">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="03b76-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="03b76-162">0</span><span class="sxs-lookup"><span data-stu-id="03b76-162">0</span></span> | <span data-ttu-id="03b76-163">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="03b76-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="03b76-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03b76-164">Remarks</span></span>

<span data-ttu-id="03b76-165">Ta funkcja zawija wywołanie do [metodę IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) metody.</span><span class="sxs-lookup"><span data-stu-id="03b76-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="03b76-166">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="03b76-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="03b76-167">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03b76-167">Requirements</span></span>

<span data-ttu-id="03b76-168">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03b76-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="03b76-169">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="03b76-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="03b76-170">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03b76-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="03b76-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03b76-171">See also</span></span>

- [<span data-ttu-id="03b76-172">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="03b76-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)