---
title: Funkcja DeleteMethod (niezarządzany wykaz interfejsów API)
description: Funkcja DeleteMethod Usuwa określoną metodę z definicji klasy modelu wspólnych informacji.
ms.date: 11/06/2017
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
ms.openlocfilehash: 5996ce41c80cb54c4fcb9104c2993c85bcc2b466
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45971744"
---
# <a name="deletemethod-function"></a><span data-ttu-id="15435-103">Funkcja DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="15435-103">DeleteMethod function</span></span>
<span data-ttu-id="15435-104">Usuwa określoną metodę z definicji klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="15435-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="15435-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15435-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="15435-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="15435-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="15435-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="15435-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="15435-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15435-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="15435-109">[in] Nazwa metody do usuwania z tabeli klasy.</span><span class="sxs-lookup"><span data-stu-id="15435-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="15435-110">`wszName` musi być wskaźnikiem do prawidłowego `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="15435-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="15435-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="15435-111">Return value</span></span>

<span data-ttu-id="15435-112">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="15435-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="15435-113">Stała</span><span class="sxs-lookup"><span data-stu-id="15435-113">Constant</span></span>  |<span data-ttu-id="15435-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="15435-114">Value</span></span>  |<span data-ttu-id="15435-115">Opis</span><span class="sxs-lookup"><span data-stu-id="15435-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="15435-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="15435-116">0x80041002</span></span> | <span data-ttu-id="15435-117">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="15435-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="15435-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="15435-118">0x80041006</span></span> | <span data-ttu-id="15435-119">Nie ma wystarczającej ilości pamięci do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="15435-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="15435-120">0</span><span class="sxs-lookup"><span data-stu-id="15435-120">0</span></span> | <span data-ttu-id="15435-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="15435-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="15435-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15435-122">Remarks</span></span>

<span data-ttu-id="15435-123">Ta funkcja zawija wywołanie do [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) metody.</span><span class="sxs-lookup"><span data-stu-id="15435-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="15435-124">Metoda usuwania nie jest obsługiwana dla [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="15435-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="15435-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15435-125">Requirements</span></span>  
 <span data-ttu-id="15435-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15435-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15435-127">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="15435-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="15435-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15435-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15435-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15435-129">See also</span></span>  
[<span data-ttu-id="15435-130">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="15435-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
