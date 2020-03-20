---
title: BlessIWbemServicesObject, funkcja (odwołanie do interfejsu API niezarządzanego)
description: Funkcja BlessIWbemServicesObject wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do obiektu IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175034"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="17c85-103">BlessIWbemServicesObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="17c85-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="17c85-104">Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonego obiektu [IWbemServices.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)</span><span class="sxs-lookup"><span data-stu-id="17c85-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="17c85-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="17c85-105">Syntax</span></span>

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="17c85-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="17c85-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="17c85-107">[w] Wskaźnik do obiektu usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="17c85-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="17c85-108">[w] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17c85-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="17c85-109">[w] Hasło skojarzone `strUser`z programem .</span><span class="sxs-lookup"><span data-stu-id="17c85-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="17c85-110">[w] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17c85-110">[in] The domain name of the user.</span></span> <span data-ttu-id="17c85-111">Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="17c85-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="17c85-112">[w] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="17c85-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="17c85-113">[w] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="17c85-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="17c85-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="17c85-114">Return value</span></span>

<span data-ttu-id="17c85-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WinError.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="17c85-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="17c85-116">Stały</span><span class="sxs-lookup"><span data-stu-id="17c85-116">Constant</span></span>  |<span data-ttu-id="17c85-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="17c85-117">Value</span></span>  |<span data-ttu-id="17c85-118">Opis</span><span class="sxs-lookup"><span data-stu-id="17c85-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="17c85-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="17c85-119">0x80070057</span></span> | <span data-ttu-id="17c85-120">Jeden lub więcej argumentów jest nieprawidłowych.</span><span class="sxs-lookup"><span data-stu-id="17c85-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="17c85-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="17c85-121">0x80004003</span></span> | <span data-ttu-id="17c85-122">Parametr `pIWbemServices` ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="17c85-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="17c85-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="17c85-123">0x80000008</span></span> | <span data-ttu-id="17c85-124">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="17c85-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="17c85-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="17c85-125">0x80000002</span></span> | <span data-ttu-id="17c85-126">Niewystarczająca ilość pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="17c85-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="17c85-127">0</span><span class="sxs-lookup"><span data-stu-id="17c85-127">0</span></span> | <span data-ttu-id="17c85-128">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="17c85-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="17c85-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17c85-129">Requirements</span></span>

 <span data-ttu-id="17c85-130">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17c85-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="17c85-131">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="17c85-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="17c85-132">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17c85-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="17c85-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17c85-133">See also</span></span>

- [<span data-ttu-id="17c85-134">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="17c85-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
