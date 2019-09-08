---
title: PutInstanceWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja PutInstanceWmi tworzy lub aktualizuje wystąpienie istniejącej klasy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798375"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="7b84e-103">PutInstanceWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="7b84e-103">PutInstanceWmi function</span></span>

<span data-ttu-id="7b84e-104">Tworzy lub aktualizuje wystąpienie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="7b84e-105">Wystąpienie jest zapisywane w repozytorium WMI.</span><span class="sxs-lookup"><span data-stu-id="7b84e-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7b84e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b84e-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="7b84e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b84e-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="7b84e-108">podczas Wskaźnik do wystąpienia do zapisania.</span><span class="sxs-lookup"><span data-stu-id="7b84e-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="7b84e-109">podczas Kombinacja flag mających wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b84e-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="7b84e-110">Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="7b84e-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7b84e-111">Stała</span><span class="sxs-lookup"><span data-stu-id="7b84e-111">Constant</span></span>  |<span data-ttu-id="7b84e-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="7b84e-112">Value</span></span>  |<span data-ttu-id="7b84e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7b84e-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="7b84e-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="7b84e-114">0x20000</span></span> | <span data-ttu-id="7b84e-115">Jeśli ta wartość jest ustawiona, usługa WMI nie przechowuje żadnych kwalifikatorów z **zmienionym** elementem.</span><span class="sxs-lookup"><span data-stu-id="7b84e-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="7b84e-116">Jeśli nie zostanie ustawiona, zakłada się, że ten obiekt nie jest zlokalizowany i wszystkie kwalifikatory są przechowywane z tym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="7b84e-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="7b84e-117">0</span><span class="sxs-lookup"><span data-stu-id="7b84e-117">0</span></span> | <span data-ttu-id="7b84e-118">Utwórz wystąpienie, jeśli nie istnieje, lub zastąp je, jeśli już istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b84e-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="7b84e-119">1</span><span class="sxs-lookup"><span data-stu-id="7b84e-119">1</span></span> | <span data-ttu-id="7b84e-120">Zaktualizuj wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7b84e-120">Update the instance.</span></span> <span data-ttu-id="7b84e-121">Wystąpienie musi istnieć, aby wywołanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7b84e-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="7b84e-122">2</span><span class="sxs-lookup"><span data-stu-id="7b84e-122">2</span></span> | <span data-ttu-id="7b84e-123">Utwórz wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7b84e-123">Create the instance.</span></span> <span data-ttu-id="7b84e-124">Wywołanie zakończy się niepowodzeniem, jeśli wystąpienie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b84e-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="7b84e-125">0x10</span><span class="sxs-lookup"><span data-stu-id="7b84e-125">0x10</span></span> | <span data-ttu-id="7b84e-126">Flaga powoduje wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="7b84e-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="7b84e-127">podczas Zazwyczaj ta wartość to `null`.</span><span class="sxs-lookup"><span data-stu-id="7b84e-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="7b84e-128">W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="7b84e-129">określoną Jeśli `null`ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="7b84e-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="7b84e-130">Jeśli `lFlags` `WBEM_S_NO_ERROR`zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca natychmiast z.</span><span class="sxs-lookup"><span data-stu-id="7b84e-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="7b84e-131">Parametr otrzymuje wskaźnik do nowego obiektu IWbemCallResult. [](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) `ppCallResult`</span><span class="sxs-lookup"><span data-stu-id="7b84e-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b84e-132">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7b84e-132">Return value</span></span>

<span data-ttu-id="7b84e-133">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="7b84e-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7b84e-134">Stała</span><span class="sxs-lookup"><span data-stu-id="7b84e-134">Constant</span></span>  |<span data-ttu-id="7b84e-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="7b84e-135">Value</span></span>  |<span data-ttu-id="7b84e-136">Opis</span><span class="sxs-lookup"><span data-stu-id="7b84e-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="7b84e-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="7b84e-137">0x80041003</span></span> | <span data-ttu-id="7b84e-138">Użytkownik nie ma uprawnienia do aktualizowania wystąpienia określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="7b84e-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7b84e-139">0x80041001</span></span> | <span data-ttu-id="7b84e-140">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="7b84e-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="7b84e-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="7b84e-141">0x80041010</span></span> | <span data-ttu-id="7b84e-142">Klasa obsługująca to wystąpienie jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="7b84e-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="7b84e-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="7b84e-143">0x80041028</span></span> | <span data-ttu-id="7b84e-144">określono dla właściwości, która nie może być `null`taka, jak taka, która jest oznaczona przez kwalifikator **Indexed** lub **NOT_NULL** . `null`</span><span class="sxs-lookup"><span data-stu-id="7b84e-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="7b84e-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="7b84e-145">0x8004100f</span></span> | <span data-ttu-id="7b84e-146">Określone wystąpienie jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="7b84e-146">The specified instance is not valid.</span></span> <span data-ttu-id="7b84e-147">(Na przykład wywoływanie `PutInstanceWmi` z klasą zwraca tę wartość).</span><span class="sxs-lookup"><span data-stu-id="7b84e-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7b84e-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7b84e-148">0x80041008</span></span> | <span data-ttu-id="7b84e-149">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="7b84e-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="7b84e-150">0x80041019</span></span> | <span data-ttu-id="7b84e-151">Określono `WBEM_FLAG_CREATE_ONLY` flagę, ale wystąpienie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b84e-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="7b84e-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7b84e-152">0x80041002</span></span> | <span data-ttu-id="7b84e-153">`WBEM_FLAG_UPDATE_ONLY`określono w `lFlags`, ale wystąpienie nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b84e-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7b84e-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7b84e-154">0x80041006</span></span> | <span data-ttu-id="7b84e-155">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="7b84e-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="7b84e-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="7b84e-156">0x80041033</span></span> | <span data-ttu-id="7b84e-157">Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="7b84e-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="7b84e-158">Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="7b84e-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="7b84e-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="7b84e-159">0x80041015</span></span> | <span data-ttu-id="7b84e-160">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="7b84e-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7b84e-161">0</span><span class="sxs-lookup"><span data-stu-id="7b84e-161">0</span></span> | <span data-ttu-id="7b84e-162">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7b84e-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7b84e-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b84e-163">Remarks</span></span>

<span data-ttu-id="7b84e-164">Ta funkcja otacza wywołanie metody [IWbemServices::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .</span><span class="sxs-lookup"><span data-stu-id="7b84e-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="7b84e-165">`PutInstanceWmi` Funkcja obsługuje tworzenie wystąpień i aktualizowanie wystąpień istniejących klas.</span><span class="sxs-lookup"><span data-stu-id="7b84e-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="7b84e-166">W zależności od sposobu `pCtx` ustawienia parametru, niektóre lub wszystkie właściwości wystąpienia są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="7b84e-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="7b84e-167">Gdy wystąpienie wskazywane przez `pInst` należy do podklasy, zarządzanie systemem Windows wywołuje wszystkich dostawców odpowiedzialnych za klasy, z których dziedziczy Klasa.</span><span class="sxs-lookup"><span data-stu-id="7b84e-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="7b84e-168">Aby oryginalne `PutInstanceWmi` żądanie powiodło się, wszyscy dostawcy muszą pomyślnie wykonać te działania.</span><span class="sxs-lookup"><span data-stu-id="7b84e-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="7b84e-169">Dostawca obsługujący klasę najwyższego poziomu w hierarchii jest nazywany pierwszym.</span><span class="sxs-lookup"><span data-stu-id="7b84e-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="7b84e-170">Kolejność wywoływania jest kontynuowana z podklasą klasy najwyższej i przechodzi z góry do dołu, dopóki zarządzanie systemem Windows osiągnie dostawcę dla klasy będącej właścicielem wystąpienia wskazywanym przez `pInst`.</span><span class="sxs-lookup"><span data-stu-id="7b84e-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="7b84e-171">Zarządzanie systemem Windows nie wywołuje dostawców dla żadnej z klas podrzędnych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7b84e-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="7b84e-172">Gdy aplikacja musi zaktualizować wystąpienie należące do hierarchii klas, `pInst` parametr musi wskazywać na wystąpienie zawierające właściwości do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="7b84e-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="7b84e-173">Oznacza to, że należy rozważyć wystąpienie docelowe, które należy do **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="7b84e-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="7b84e-174">Wystąpienie **ClassB** dziedziczy z **ClassA**, a **ClassA** definiuje Właściwość **propa**.</span><span class="sxs-lookup"><span data-stu-id="7b84e-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="7b84e-175">Jeśli aplikacja chce wprowadzić zmiany do wartości **propa** w wystąpieniu **ClassB** , musi ustawić `pInst` to wystąpienie, a nie wystąpienie elementu **ClassA**.</span><span class="sxs-lookup"><span data-stu-id="7b84e-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="7b84e-176">Wywoływanie `PutInstanceWmi` wystąpienia klasy abstrakcyjnej jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="7b84e-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="7b84e-177">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="7b84e-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b84e-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b84e-178">Requirements</span></span>

<span data-ttu-id="7b84e-179">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b84e-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7b84e-180">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7b84e-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="7b84e-181">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7b84e-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7b84e-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b84e-182">See also</span></span>

- [<span data-ttu-id="7b84e-183">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="7b84e-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
