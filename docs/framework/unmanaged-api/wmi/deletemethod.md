---
title: Funkcja DeleteMethod (odwołanie do niezarządzanego interfejsu API)
description: Funkcja DeleteMethod usuwa określoną metodę z definicji klasy CIM.
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
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174995"
---
# <a name="deletemethod-function"></a><span data-ttu-id="94477-103">DeleteMethod, funkcja</span><span class="sxs-lookup"><span data-stu-id="94477-103">DeleteMethod function</span></span>
<span data-ttu-id="94477-104">Usuwa określoną metodę z definicji klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="94477-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="94477-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="94477-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="94477-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="94477-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="94477-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="94477-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="94477-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="94477-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="94477-109">[w] Nazwa metody do usunięcia z tabeli klas.</span><span class="sxs-lookup"><span data-stu-id="94477-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="94477-110">`wszName`musi być wskaźnikiem `LPCWSTR`do prawidłowego .</span><span class="sxs-lookup"><span data-stu-id="94477-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="94477-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="94477-111">Return value</span></span>

<span data-ttu-id="94477-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="94477-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="94477-113">Stały</span><span class="sxs-lookup"><span data-stu-id="94477-113">Constant</span></span>  |<span data-ttu-id="94477-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="94477-114">Value</span></span>  |<span data-ttu-id="94477-115">Opis</span><span class="sxs-lookup"><span data-stu-id="94477-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="94477-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="94477-116">0x80041002</span></span> | <span data-ttu-id="94477-117">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="94477-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="94477-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="94477-118">0x80041006</span></span> | <span data-ttu-id="94477-119">Nie ma wystarczającej ilości pamięci, aby zakończyć operację.</span><span class="sxs-lookup"><span data-stu-id="94477-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="94477-120">0</span><span class="sxs-lookup"><span data-stu-id="94477-120">0</span></span> | <span data-ttu-id="94477-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="94477-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="94477-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94477-122">Remarks</span></span>

<span data-ttu-id="94477-123">Ta funkcja zawija wywołanie [metody IWbemClassObject::DeleteMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod)</span><span class="sxs-lookup"><span data-stu-id="94477-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="94477-124">Usuwanie metody nie jest obsługiwane dla wskaźników [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) które wskazują na wystąpienia CIM.</span><span class="sxs-lookup"><span data-stu-id="94477-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="94477-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94477-125">Requirements</span></span>  
 <span data-ttu-id="94477-126">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94477-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94477-127">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="94477-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="94477-128">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94477-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94477-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94477-129">See also</span></span>

- [<span data-ttu-id="94477-130">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="94477-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
