---
title: "Funkcja DeleteMethod (niezarządzany wykaz interfejsów API)"
description: "Funkcja DeleteMethod usuwa określonej metody z definicji klasy modelu wspólnych informacji."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03b147d2fd76e34c6152a0b41ee14319811e9300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deletemethod-function"></a><span data-ttu-id="493ff-103">Funkcja DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="493ff-103">DeleteMethod function</span></span>
<span data-ttu-id="493ff-104">Usuwa określonej metody z definicji klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="493ff-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="493ff-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="493ff-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="493ff-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="493ff-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="493ff-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="493ff-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="493ff-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="493ff-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="493ff-109">[in] Nazwa metody do usunięcia z tabeli klasy.</span><span class="sxs-lookup"><span data-stu-id="493ff-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="493ff-110">`wszName`musi być wskaźnikiem do prawidłowej `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="493ff-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="493ff-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="493ff-111">Return value</span></span>

<span data-ttu-id="493ff-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="493ff-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="493ff-113">Stała</span><span class="sxs-lookup"><span data-stu-id="493ff-113">Constant</span></span>  |<span data-ttu-id="493ff-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="493ff-114">Value</span></span>  |<span data-ttu-id="493ff-115">Opis</span><span class="sxs-lookup"><span data-stu-id="493ff-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="493ff-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="493ff-116">0x80041002</span></span> | <span data-ttu-id="493ff-117">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="493ff-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="493ff-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="493ff-118">0x80041006</span></span> | <span data-ttu-id="493ff-119">Nie ma wystarczającej ilości pamięci do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="493ff-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="493ff-120">0</span><span class="sxs-lookup"><span data-stu-id="493ff-120">0</span></span> | <span data-ttu-id="493ff-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="493ff-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="493ff-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="493ff-122">Remarks</span></span>

<span data-ttu-id="493ff-123">Ta funkcja jest zawijana wywołanie [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="493ff-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="493ff-124">Usuwanie — metoda nie jest obsługiwane dla [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskaźników, które wskazują wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="493ff-124">Method deletion is not supported for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="493ff-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="493ff-125">Requirements</span></span>  
 <span data-ttu-id="493ff-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="493ff-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493ff-127">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="493ff-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="493ff-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="493ff-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493ff-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="493ff-129">See also</span></span>  
[<span data-ttu-id="493ff-130">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="493ff-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
