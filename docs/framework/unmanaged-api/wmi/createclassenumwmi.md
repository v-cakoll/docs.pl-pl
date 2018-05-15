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
ms.openlocfilehash: 3f84902586a2b940d52eb6365a141af61af802dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="c45e0-103">Funkcja CreateClassEnumWmi</span><span class="sxs-lookup"><span data-stu-id="c45e0-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="c45e0-104">Zwraca moduł wyliczający dla wszystkich klas, które spełniają kryteria określonego zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="c45e0-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c45e0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c45e0-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="c45e0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c45e0-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="c45e0-107">[in] Jeśli nie `null` lub puste, określa nazwę klasy nadrzędnej; modułu wyliczającego zwraca tylko podklasy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c45e0-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="c45e0-108">Jeśli jest `null` lub jest pusty i `lFlags` WBEM_FLAG_SHALLOW, zwraca tylko klasy najwyższego poziomu (klasy z klasy nadrzędnej, nie).</span><span class="sxs-lookup"><span data-stu-id="c45e0-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="c45e0-109">Jeśli jest `null` lub jest pusty i `lFlags` jest `WBEM_FLAG_DEEP`, zwraca wszystkie klasy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c45e0-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="c45e0-110">[in] Kombinacja flag, które wpływają na działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="c45e0-111">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="c45e0-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="c45e0-112">Stała</span><span class="sxs-lookup"><span data-stu-id="c45e0-112">Constant</span></span>  |<span data-ttu-id="c45e0-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="c45e0-113">Value</span></span>  |<span data-ttu-id="c45e0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c45e0-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="c45e0-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="c45e0-115">0x20000</span></span> | <span data-ttu-id="c45e0-116">Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="c45e0-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="c45e0-117">Jeśli nie zestawu, funkcja pobiera tylko kwalifikatory przechowywane w przestrzeni nazw bezpośrednim.</span><span class="sxs-lookup"><span data-stu-id="c45e0-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="c45e0-118">0</span><span class="sxs-lookup"><span data-stu-id="c45e0-118">0</span></span> | <span data-ttu-id="c45e0-119">Wyliczenie zawiera podklasami w hierarchii, ale nie do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c45e0-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="c45e0-120">1</span><span class="sxs-lookup"><span data-stu-id="c45e0-120">1</span></span> | <span data-ttu-id="c45e0-121">Wyliczenie zawiera tylko czysty wystąpienia tej klasy i wyklucza wszystkie wystąpienia podklas, które dostarczają właściwości nie można odnaleźć w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="c45e0-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="c45e0-122">0x10</span><span class="sxs-lookup"><span data-stu-id="c45e0-122">0x10</span></span> | <span data-ttu-id="c45e0-123">Flaga powoduje Półsynchroniczne wywołania.</span><span class="sxs-lookup"><span data-stu-id="c45e0-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="c45e0-124">0x20</span><span class="sxs-lookup"><span data-stu-id="c45e0-124">0x20</span></span> | <span data-ttu-id="c45e0-125">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c45e0-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="c45e0-126">Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="c45e0-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="c45e0-127">0</span><span class="sxs-lookup"><span data-stu-id="c45e0-127">0</span></span> | <span data-ttu-id="c45e0-128">WMI zachowuje wskaźników do obiektów w enumration, dopóki ich wydania.</span><span class="sxs-lookup"><span data-stu-id="c45e0-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="c45e0-129">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="c45e0-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="c45e0-130">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="c45e0-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="c45e0-131">W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="c45e0-131">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="c45e0-132">[out] Uzyskuje wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c45e0-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="c45e0-133">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-133">[in] The authorization level.</span></span>

<span data-ttu-id="c45e0-134">`impLevel` [in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="c45e0-135">[in] Wskaźnik do [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c45e0-135">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="c45e0-136">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c45e0-136">[in] The user name.</span></span> <span data-ttu-id="c45e0-137">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="c45e0-138">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="c45e0-138">[in] The password.</span></span> <span data-ttu-id="c45e0-139">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="c45e0-140">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c45e0-140">[in] The domain name of the user.</span></span> <span data-ttu-id="c45e0-141">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="c45e0-142">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c45e0-142">Return value</span></span>

<span data-ttu-id="c45e0-143">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="c45e0-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c45e0-144">Stała</span><span class="sxs-lookup"><span data-stu-id="c45e0-144">Constant</span></span>  |<span data-ttu-id="c45e0-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="c45e0-145">Value</span></span>  |<span data-ttu-id="c45e0-146">Opis</span><span class="sxs-lookup"><span data-stu-id="c45e0-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="c45e0-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="c45e0-147">0x80041003</span></span> | <span data-ttu-id="c45e0-148">Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="c45e0-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c45e0-149">0x80041001</span></span> | <span data-ttu-id="c45e0-150">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="c45e0-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="c45e0-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="c45e0-151">0x80041010</span></span> | <span data-ttu-id="c45e0-152">`strSuperClass` nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c45e0-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c45e0-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c45e0-153">0x80041008</span></span> | <span data-ttu-id="c45e0-154">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="c45e0-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c45e0-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c45e0-155">0x80041006</span></span> | <span data-ttu-id="c45e0-156">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="c45e0-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="c45e0-157">0x80041033</span></span> | <span data-ttu-id="c45e0-158">Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="c45e0-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="c45e0-159">Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="c45e0-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="c45e0-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="c45e0-160">0x80041015</span></span> | <span data-ttu-id="c45e0-161">Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c45e0-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c45e0-162">0</span><span class="sxs-lookup"><span data-stu-id="c45e0-162">0</span></span> | <span data-ttu-id="c45e0-163">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c45e0-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c45e0-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c45e0-164">Remarks</span></span>

<span data-ttu-id="c45e0-165">Ta funkcja jest zawijana wywołanie [metodę IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="c45e0-165">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="c45e0-166">Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="c45e0-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="c45e0-167">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c45e0-167">Requirements</span></span>  
 <span data-ttu-id="c45e0-168">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c45e0-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c45e0-169">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c45e0-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c45e0-170">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c45e0-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45e0-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c45e0-171">See also</span></span>  
[<span data-ttu-id="c45e0-172">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="c45e0-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
