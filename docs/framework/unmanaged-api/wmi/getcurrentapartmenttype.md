---
title: GetCurrentApartmentType, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetCurrentApartmentType pobiera typ mieszkania, w którym wykonuje się obiekt wywołujący.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176828"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="d0b33-103">GetCurrentApartmentType, funkcja</span><span class="sxs-lookup"><span data-stu-id="d0b33-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="d0b33-104">Pobiera typ mieszkania, w którym wywoływany jest.</span><span class="sxs-lookup"><span data-stu-id="d0b33-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d0b33-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0b33-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="d0b33-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0b33-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d0b33-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="d0b33-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d0b33-108">[w] Wskaźnik do wystąpienia [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)</span><span class="sxs-lookup"><span data-stu-id="d0b33-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="d0b33-109">[na zewnątrz] Wskaźnik do wartości wyliczenia [APTTYPE,](/windows/win32/api/objidlbase/ne-objidlbase-apttype) która wskazuje mieszkanie wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d0b33-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0b33-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0b33-110">Return value</span></span>

|<span data-ttu-id="d0b33-111">Stały</span><span class="sxs-lookup"><span data-stu-id="d0b33-111">Constant</span></span>  |<span data-ttu-id="d0b33-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="d0b33-112">Value</span></span>  |<span data-ttu-id="d0b33-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d0b33-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="d0b33-114">0</span><span class="sxs-lookup"><span data-stu-id="d0b33-114">0</span></span> | <span data-ttu-id="d0b33-115">Funkcja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0b33-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="d0b33-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="d0b33-116">0x80000008</span></span> | <span data-ttu-id="d0b33-117">Dzwoniący nie wykonuje w mieszkaniu.</span><span class="sxs-lookup"><span data-stu-id="d0b33-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d0b33-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0b33-118">Remarks</span></span>

<span data-ttu-id="d0b33-119">Ta funkcja zawija wywołanie metody [IComThreadingInfo::GetCurrentApartmentType.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)</span><span class="sxs-lookup"><span data-stu-id="d0b33-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0b33-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0b33-120">Requirements</span></span>  
 <span data-ttu-id="d0b33-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0b33-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b33-122">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d0b33-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d0b33-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b33-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b33-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0b33-124">See also</span></span>

- [<span data-ttu-id="d0b33-125">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d0b33-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
