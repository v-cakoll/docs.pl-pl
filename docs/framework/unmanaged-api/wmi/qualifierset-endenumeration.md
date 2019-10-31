---
title: QualifierSet_EndEnumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_EndEnumeration kończy Wyliczenie.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 82627fa416f71e123ed2c03bae4584e4433310eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127288"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="30bed-103">QualifierSet_EndEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="30bed-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="30bed-104">Kończy Wyliczenie rozpoczęte z wywołaniem funkcji [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="30bed-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="30bed-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="30bed-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="30bed-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="30bed-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="30bed-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="30bed-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="30bed-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="30bed-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="30bed-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="30bed-109">Return value</span></span>

<span data-ttu-id="30bed-110">Następująca wartość zwrócona przez tę funkcję jest zdefiniowana w pliku nagłówkowym *WbemCli. h* lub można ją zdefiniować jako stałą w kodzie:</span><span class="sxs-lookup"><span data-stu-id="30bed-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="30bed-111">Stała</span><span class="sxs-lookup"><span data-stu-id="30bed-111">Constant</span></span>  |<span data-ttu-id="30bed-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="30bed-112">Value</span></span>  |<span data-ttu-id="30bed-113">Opis</span><span class="sxs-lookup"><span data-stu-id="30bed-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="30bed-114">0</span><span class="sxs-lookup"><span data-stu-id="30bed-114">0</span></span> | <span data-ttu-id="30bed-115">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="30bed-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="30bed-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30bed-116">Remarks</span></span>

<span data-ttu-id="30bed-117">Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .</span><span class="sxs-lookup"><span data-stu-id="30bed-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="30bed-118">To wywołanie jest zalecane, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="30bed-118">This call is recommended, but not required.</span></span> <span data-ttu-id="30bed-119">Natychmiast zwalnia zasoby skojarzone z wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="30bed-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="30bed-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30bed-120">Requirements</span></span>  

<span data-ttu-id="30bed-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30bed-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="30bed-122">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="30bed-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="30bed-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30bed-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30bed-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30bed-124">See also</span></span>

- [<span data-ttu-id="30bed-125">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="30bed-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
