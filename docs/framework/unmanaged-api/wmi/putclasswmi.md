---
title: PutClassWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja PutClassWmi tworzy nową klasę lub aktualizuje istniejącą.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fcf879705135e0093868b48580a37f9d46aa594
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798381"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="d271e-103">PutClassWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="d271e-103">PutClassWmi function</span></span>

<span data-ttu-id="d271e-104">Tworzy nową klasę lub aktualizuje istniejącą.</span><span class="sxs-lookup"><span data-stu-id="d271e-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d271e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d271e-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="d271e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d271e-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="d271e-107">podczas Wskaźnik do prawidłowej definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="d271e-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="d271e-108">Należy ją poprawnie zainicjować przy użyciu wszystkich wymaganych wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d271e-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="d271e-109">podczas Kombinacja flag mających wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d271e-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="d271e-110">Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d271e-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d271e-111">Stała</span><span class="sxs-lookup"><span data-stu-id="d271e-111">Constant</span></span>  |<span data-ttu-id="d271e-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="d271e-112">Value</span></span>  |<span data-ttu-id="d271e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d271e-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="d271e-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="d271e-114">0x20000</span></span> | <span data-ttu-id="d271e-115">Jeśli ta wartość jest ustawiona, usługa WMI nie przechowuje żadnych kwalifikatorów z zmienionym elementem.</span><span class="sxs-lookup"><span data-stu-id="d271e-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="d271e-116">Jeśli nie zostanie ustawiona, zakłada się, że ten obiekt nie jest zlokalizowany i wszystkie kwalifikatory są przechowywane z tym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="d271e-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="d271e-117">0</span><span class="sxs-lookup"><span data-stu-id="d271e-117">0</span></span> | <span data-ttu-id="d271e-118">Utwórz klasę, jeśli nie istnieje, lub Zastąp ją, jeśli już istnieje.</span><span class="sxs-lookup"><span data-stu-id="d271e-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="d271e-119">1</span><span class="sxs-lookup"><span data-stu-id="d271e-119">1</span></span> | <span data-ttu-id="d271e-120">Zaktualizuj klasę.</span><span class="sxs-lookup"><span data-stu-id="d271e-120">Update the class.</span></span> <span data-ttu-id="d271e-121">Klasa musi istnieć, aby wywołanie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d271e-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="d271e-122">2</span><span class="sxs-lookup"><span data-stu-id="d271e-122">2</span></span> | <span data-ttu-id="d271e-123">Utwórz klasę.</span><span class="sxs-lookup"><span data-stu-id="d271e-123">Create the class.</span></span> <span data-ttu-id="d271e-124">Wywołanie zakończy się niepowodzeniem, jeśli Klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="d271e-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="d271e-125">0x10</span><span class="sxs-lookup"><span data-stu-id="d271e-125">0x10</span></span> | <span data-ttu-id="d271e-126">Flaga powoduje wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d271e-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="d271e-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="d271e-127">0x10000</span></span> | <span data-ttu-id="d271e-128">Dostawcy wypychania muszą określać tę flagę podczas wywoływania `PutClassWmi` , aby wskazać, że ta klasa została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="d271e-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="d271e-129">0</span><span class="sxs-lookup"><span data-stu-id="d271e-129">0</span></span> | <span data-ttu-id="d271e-130">Umożliwia zaktualizowanie klasy, jeśli nie ma klas pochodnych i nie ma wystąpień tej klasy.</span><span class="sxs-lookup"><span data-stu-id="d271e-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="d271e-131">Pozwala także na aktualizacje we wszystkich przypadkach, gdy zmiana dotyczy tylko nieistotnych kwalifikatorów, takich jak kwalifikator opisu.</span><span class="sxs-lookup"><span data-stu-id="d271e-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="d271e-132">Jeśli klasa ma wystąpienia lub zmiany są istotnymi kwalifikatorami, aktualizacja kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d271e-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="d271e-133">0x20</span><span class="sxs-lookup"><span data-stu-id="d271e-133">0x20</span></span> | <span data-ttu-id="d271e-134">Zezwala na aktualizacje klas, nawet jeśli istnieją klasy podrzędne, o ile zmiana nie powoduje żadnych konfliktów z klasami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="d271e-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="d271e-135">Na przykład ta flaga umożliwia dodanie nowej właściwości do klasy podstawowej, która nie została wcześniej wymieniona w żadnej z klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d271e-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="d271e-136">Jeśli klasa ma wystąpienia, aktualizacja kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d271e-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="d271e-137">0x40</span><span class="sxs-lookup"><span data-stu-id="d271e-137">0x40</span></span> | <span data-ttu-id="d271e-138">wymusza aktualizacje klas, gdy istnieją sprzeczne klasy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="d271e-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="d271e-139">Na przykład ta flaga wymusza aktualizację, jeśli kwalifikator klasy jest zdefiniowany w klasie podrzędnej, a Klasa bazowa próbuje dodać ten sam kwalifikator, który powoduje konflikt z istniejącym elementem.</span><span class="sxs-lookup"><span data-stu-id="d271e-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="d271e-140">W trybie wymuszania konflikt TIS jest rozwiązywany przez usunięcie kwalifikatora powodującego konflikt w klasie podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="d271e-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="d271e-141">podczas Zazwyczaj ta wartość to `null`.</span><span class="sxs-lookup"><span data-stu-id="d271e-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="d271e-142">W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.</span><span class="sxs-lookup"><span data-stu-id="d271e-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="d271e-143">określoną Jeśli `null`ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="d271e-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="d271e-144">Jeśli `lFlags` `WBEM_S_NO_ERROR`zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca natychmiast z.</span><span class="sxs-lookup"><span data-stu-id="d271e-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="d271e-145">Parametr otrzymuje wskaźnik do nowego obiektu IWbemCallResult. [](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) `ppCallResult`</span><span class="sxs-lookup"><span data-stu-id="d271e-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="d271e-146">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d271e-146">Return value</span></span>

<span data-ttu-id="d271e-147">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d271e-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d271e-148">Stała</span><span class="sxs-lookup"><span data-stu-id="d271e-148">Constant</span></span>  |<span data-ttu-id="d271e-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="d271e-149">Value</span></span>  |<span data-ttu-id="d271e-150">Opis</span><span class="sxs-lookup"><span data-stu-id="d271e-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="d271e-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="d271e-151">0x80041003</span></span> | <span data-ttu-id="d271e-152">Użytkownik nie ma uprawnienia do tworzenia lub modyfikowania klas.</span><span class="sxs-lookup"><span data-stu-id="d271e-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="d271e-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d271e-153">0x80041001</span></span> | <span data-ttu-id="d271e-154">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="d271e-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="d271e-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="d271e-155">0x80041010</span></span> | <span data-ttu-id="d271e-156">Określona Klasa jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="d271e-156">The specified class is not valid.</span></span> <span data-ttu-id="d271e-157">Zazwyczaj oznacza to, że `pObject` określa obiekt wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d271e-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d271e-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d271e-158">0x80041008</span></span> | <span data-ttu-id="d271e-159">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d271e-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="d271e-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="d271e-160">0x80041016</span></span> | <span data-ttu-id="d271e-161">Określona nazwa klasy jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="d271e-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="d271e-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="d271e-162">0x80041025</span></span> | <span data-ttu-id="d271e-163">Podjęto próbę dokonania zmiany, która spowodowałaby unieważnienie podklasy.</span><span class="sxs-lookup"><span data-stu-id="d271e-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="d271e-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="d271e-164">0x80041019</span></span> | <span data-ttu-id="d271e-165">Określono `WBEM_FLAG_CREATE_ONLY` flagę, ale Klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="d271e-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="d271e-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d271e-166">0x80041002</span></span> | <span data-ttu-id="d271e-167">`WBEM_FLAG_UPDATE_ONLY`określono w `lFlags`i nie znaleziono klasy.</span><span class="sxs-lookup"><span data-stu-id="d271e-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="d271e-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="d271e-168">0x80041020</span></span> | <span data-ttu-id="d271e-169">Nie wszystkie wymagane właściwości dla klas.</span><span class="sxs-lookup"><span data-stu-id="d271e-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d271e-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d271e-170">0x80041006</span></span> | <span data-ttu-id="d271e-171">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="d271e-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="d271e-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="d271e-172">0x80041033</span></span> | <span data-ttu-id="d271e-173">Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="d271e-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="d271e-174">Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="d271e-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="d271e-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="d271e-175">0x80041015</span></span> | <span data-ttu-id="d271e-176">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d271e-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d271e-177">0</span><span class="sxs-lookup"><span data-stu-id="d271e-177">0</span></span> | <span data-ttu-id="d271e-178">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d271e-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="d271e-179">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d271e-179">Remarks</span></span>

<span data-ttu-id="d271e-180">Ta funkcja otacza wywołanie metody [IWbemServices::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .</span><span class="sxs-lookup"><span data-stu-id="d271e-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="d271e-181">Użytkownik nie może tworzyć klas o nazwach zaczynających się lub kończących znakiem podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="d271e-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="d271e-182">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="d271e-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d271e-183">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d271e-183">Requirements</span></span>

<span data-ttu-id="d271e-184">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d271e-184">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d271e-185">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d271e-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="d271e-186">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d271e-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d271e-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d271e-187">See also</span></span>

- [<span data-ttu-id="d271e-188">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d271e-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
