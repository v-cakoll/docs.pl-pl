---
title: funkcja QualifierSet_EndEnumeration (odwołanie do interfejsu API niezarządzanego)
description: Funkcja QualifierSet_EndEnumeration kończy wyliczenie.
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
ms.openlocfilehash: c606580ff2e02c5659c14b134b1a17a65651952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176750"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="6da7e-103">QualifierSet_EndEnumeration funkcja</span><span class="sxs-lookup"><span data-stu-id="6da7e-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="6da7e-104">Kończy wyliczenie rozpoczęte wywołaniem funkcji [QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="6da7e-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6da7e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6da7e-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="6da7e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6da7e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6da7e-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="6da7e-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="6da7e-108">`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="6da7e-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="6da7e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6da7e-109">Return value</span></span>

<span data-ttu-id="6da7e-110">Następująca wartość zwracana przez tę funkcję jest zdefiniowana w pliku nagłówkowym *WbemCli.h* lub można zdefiniować ją jako stałą w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6da7e-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="6da7e-111">Stały</span><span class="sxs-lookup"><span data-stu-id="6da7e-111">Constant</span></span>  |<span data-ttu-id="6da7e-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="6da7e-112">Value</span></span>  |<span data-ttu-id="6da7e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6da7e-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6da7e-114">0</span><span class="sxs-lookup"><span data-stu-id="6da7e-114">0</span></span> | <span data-ttu-id="6da7e-115">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6da7e-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6da7e-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6da7e-116">Remarks</span></span>

<span data-ttu-id="6da7e-117">Ta funkcja zawija wywołanie [metody IWbemQualifierSet::EndEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)</span><span class="sxs-lookup"><span data-stu-id="6da7e-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="6da7e-118">To wywołanie jest zalecane, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="6da7e-118">This call is recommended, but not required.</span></span> <span data-ttu-id="6da7e-119">Natychmiast zwalnia zasoby skojarzone z wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="6da7e-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="6da7e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6da7e-120">Requirements</span></span>  

<span data-ttu-id="6da7e-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6da7e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="6da7e-122">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6da7e-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="6da7e-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6da7e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6da7e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6da7e-124">See also</span></span>

- [<span data-ttu-id="6da7e-125">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="6da7e-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
