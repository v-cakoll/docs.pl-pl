---
title: Funkcja BlessIWbemServices (niezarządzany wykaz interfejsów API)
description: Funkcja BlessIWbemServices wskazuje, czy poświadczenia użytkownika zezwolić na dostęp do klasy IWbemServices.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb83bc3c0c7724dbcd3133465d4e7ad3a9eea3a9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636504"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="5c570-103">BlessIWbemServices, funkcja</span><span class="sxs-lookup"><span data-stu-id="5c570-103">BlessIWbemServices function</span></span>
<span data-ttu-id="5c570-104">Wskazuje, czy poświadczenia użytkownika zezwolić na dostęp do określonego [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) klasy.</span><span class="sxs-lookup"><span data-stu-id="5c570-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5c570-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c570-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="5c570-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c570-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="5c570-107">[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiektu, dla których wymagane są uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="5c570-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="5c570-108">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5c570-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="5c570-109">[in] Hasło skojarzone z `strUser`.</span><span class="sxs-lookup"><span data-stu-id="5c570-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="5c570-110">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5c570-110">[in] The domain name of the user.</span></span> <span data-ttu-id="5c570-111">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="5c570-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="5c570-112">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="5c570-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="5c570-113">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="5c570-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c570-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c570-114">Return value</span></span>

<span data-ttu-id="5c570-115">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WinError.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5c570-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5c570-116">Stała</span><span class="sxs-lookup"><span data-stu-id="5c570-116">Constant</span></span>  |<span data-ttu-id="5c570-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c570-117">Value</span></span>  |<span data-ttu-id="5c570-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5c570-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="5c570-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="5c570-119">0x80070057</span></span> | <span data-ttu-id="5c570-120">Jeden lub więcej argumentów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="5c570-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="5c570-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="5c570-121">0x80004003</span></span> | <span data-ttu-id="5c570-122">`pIWbemServices` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="5c570-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="5c570-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="5c570-123">0x80000008</span></span> | <span data-ttu-id="5c570-124">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="5c570-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="5c570-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="5c570-125">0x80000002</span></span> | <span data-ttu-id="5c570-126">Ma wystarczającej ilości pamięci do wykonania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="5c570-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="5c570-127">0</span><span class="sxs-lookup"><span data-stu-id="5c570-127">0</span></span> | <span data-ttu-id="5c570-128">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5c570-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="5c570-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c570-129">Requirements</span></span>  

 <span data-ttu-id="5c570-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c570-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c570-131">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5c570-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5c570-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5c570-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c570-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c570-133">See also</span></span>

- [<span data-ttu-id="5c570-134">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5c570-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
