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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798322"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="746e1-103">QualifierSet_EndEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="746e1-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="746e1-104">Kończy Wyliczenie rozpoczęte z wywołaniem funkcji [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="746e1-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="746e1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="746e1-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="746e1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="746e1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="746e1-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="746e1-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="746e1-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="746e1-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="746e1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="746e1-109">Return value</span></span>

<span data-ttu-id="746e1-110">Następująca wartość zwrócona przez tę funkcję jest zdefiniowana w pliku nagłówkowym *WbemCli. h* lub można ją zdefiniować jako stałą w kodzie:</span><span class="sxs-lookup"><span data-stu-id="746e1-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="746e1-111">Stała</span><span class="sxs-lookup"><span data-stu-id="746e1-111">Constant</span></span>  |<span data-ttu-id="746e1-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="746e1-112">Value</span></span>  |<span data-ttu-id="746e1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="746e1-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="746e1-114">0</span><span class="sxs-lookup"><span data-stu-id="746e1-114">0</span></span> | <span data-ttu-id="746e1-115">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="746e1-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="746e1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="746e1-116">Remarks</span></span>

<span data-ttu-id="746e1-117">Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .</span><span class="sxs-lookup"><span data-stu-id="746e1-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="746e1-118">To wywołanie jest zalecane, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="746e1-118">This call is recommended, but not required.</span></span> <span data-ttu-id="746e1-119">Natychmiast zwalnia zasoby skojarzone z wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="746e1-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="746e1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="746e1-120">Requirements</span></span>  

<span data-ttu-id="746e1-121">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="746e1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="746e1-122">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="746e1-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="746e1-123">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="746e1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746e1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="746e1-124">See also</span></span>

- [<span data-ttu-id="746e1-125">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="746e1-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
