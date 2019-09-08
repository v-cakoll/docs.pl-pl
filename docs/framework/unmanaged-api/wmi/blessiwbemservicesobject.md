---
title: BlessIWbemServicesObject — funkcja (niezarządzana dokumentacja interfejsu API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94c6f47e67cf22f189719a8a9f56e830ee90227c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798727"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="fafac-103">BlessIWbemServicesObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="fafac-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="fafac-104">Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonego obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) .</span><span class="sxs-lookup"><span data-stu-id="fafac-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fafac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fafac-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="fafac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fafac-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="fafac-107">podczas Wskaźnik do obiektu usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="fafac-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="fafac-108">podczas Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fafac-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="fafac-109">podczas Hasło skojarzone z `strUser`.</span><span class="sxs-lookup"><span data-stu-id="fafac-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="fafac-110">podczas Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fafac-110">[in] The domain name of the user.</span></span> <span data-ttu-id="fafac-111">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="fafac-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="fafac-112">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="fafac-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="fafac-113">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="fafac-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="fafac-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fafac-114">Return value</span></span>

<span data-ttu-id="fafac-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *Winerror. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="fafac-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fafac-116">Stała</span><span class="sxs-lookup"><span data-stu-id="fafac-116">Constant</span></span>  |<span data-ttu-id="fafac-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="fafac-117">Value</span></span>  |<span data-ttu-id="fafac-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fafac-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="fafac-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="fafac-119">0x80070057</span></span> | <span data-ttu-id="fafac-120">Co najmniej jeden argument jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="fafac-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="fafac-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="fafac-121">0x80004003</span></span> | <span data-ttu-id="fafac-122">`pIWbemServices`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="fafac-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="fafac-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="fafac-123">0x80000008</span></span> | <span data-ttu-id="fafac-124">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="fafac-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="fafac-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="fafac-125">0x80000002</span></span> | <span data-ttu-id="fafac-126">Za mało dostępnej pamięci, aby wykonać tę operację.</span><span class="sxs-lookup"><span data-stu-id="fafac-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="fafac-127">0</span><span class="sxs-lookup"><span data-stu-id="fafac-127">0</span></span> | <span data-ttu-id="fafac-128">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fafac-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="fafac-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fafac-129">Requirements</span></span>

 <span data-ttu-id="fafac-130">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fafac-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="fafac-131">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fafac-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="fafac-132">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fafac-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fafac-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fafac-133">See also</span></span>

- [<span data-ttu-id="fafac-134">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="fafac-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
