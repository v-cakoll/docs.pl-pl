---
title: Funkcja BlessIWbemServices (odwołanie do interfejsu API niezarządzanego)
description: Funkcja BlessIWbemServices wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do klasy IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176867"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="7c597-103">BlessIWbemServices, funkcja</span><span class="sxs-lookup"><span data-stu-id="7c597-103">BlessIWbemServices function</span></span>
<span data-ttu-id="7c597-104">Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonej klasy [IWbemServices.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)</span><span class="sxs-lookup"><span data-stu-id="7c597-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7c597-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c597-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="7c597-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c597-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="7c597-107">[w] Wskaźnik do [obiektu IWbemServices,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) dla którego wymagane są uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="7c597-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="7c597-108">[w] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7c597-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="7c597-109">[w] Hasło skojarzone `strUser`z programem .</span><span class="sxs-lookup"><span data-stu-id="7c597-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="7c597-110">[w] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7c597-110">[in] The domain name of the user.</span></span> <span data-ttu-id="7c597-111">Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)</span><span class="sxs-lookup"><span data-stu-id="7c597-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="7c597-112">[w] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="7c597-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="7c597-113">[w] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7c597-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c597-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c597-114">Return value</span></span>

<span data-ttu-id="7c597-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WinError.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="7c597-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7c597-116">Stały</span><span class="sxs-lookup"><span data-stu-id="7c597-116">Constant</span></span>  |<span data-ttu-id="7c597-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="7c597-117">Value</span></span>  |<span data-ttu-id="7c597-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7c597-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="7c597-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="7c597-119">0x80070057</span></span> | <span data-ttu-id="7c597-120">Jeden lub więcej argumentów jest nieprawidłowych.</span><span class="sxs-lookup"><span data-stu-id="7c597-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="7c597-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="7c597-121">0x80004003</span></span> | <span data-ttu-id="7c597-122">Parametr `pIWbemServices` ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="7c597-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="7c597-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="7c597-123">0x80000008</span></span> | <span data-ttu-id="7c597-124">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="7c597-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="7c597-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="7c597-125">0x80000002</span></span> | <span data-ttu-id="7c597-126">Niewystarczająca ilość pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="7c597-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="7c597-127">0</span><span class="sxs-lookup"><span data-stu-id="7c597-127">0</span></span> | <span data-ttu-id="7c597-128">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7c597-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7c597-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c597-129">Requirements</span></span>  

 <span data-ttu-id="7c597-130">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c597-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c597-131">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7c597-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7c597-132">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7c597-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c597-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c597-133">See also</span></span>

- [<span data-ttu-id="7c597-134">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="7c597-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
