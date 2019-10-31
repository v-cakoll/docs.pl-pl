---
title: GetCurrentApartmentType — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetCurrentApartmentType Pobiera typ apartamentu, w którym wykonywany jest obiekt wywołujący.
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
ms.openlocfilehash: 6ecd2b49d6850a8fae25ddca54f855fdda2ccabb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120355"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="2ecd7-103">GetCurrentApartmentType, funkcja</span><span class="sxs-lookup"><span data-stu-id="2ecd7-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="2ecd7-104">Pobiera typ apartamentu, w którym wykonywany jest obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="2ecd7-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2ecd7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ecd7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="2ecd7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ecd7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2ecd7-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="2ecd7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2ecd7-108">podczas Wskaźnik do wystąpienia [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .</span><span class="sxs-lookup"><span data-stu-id="2ecd7-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="2ecd7-109">określoną Wskaźnik do [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) wartości wyliczenia, który wskazuje Apartament obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2ecd7-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ecd7-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ecd7-110">Return value</span></span>

|<span data-ttu-id="2ecd7-111">Stała</span><span class="sxs-lookup"><span data-stu-id="2ecd7-111">Constant</span></span>  |<span data-ttu-id="2ecd7-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="2ecd7-112">Value</span></span>  |<span data-ttu-id="2ecd7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2ecd7-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="2ecd7-114">0</span><span class="sxs-lookup"><span data-stu-id="2ecd7-114">0</span></span> | <span data-ttu-id="2ecd7-115">Funkcja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2ecd7-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="2ecd7-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="2ecd7-116">0x80000008</span></span> | <span data-ttu-id="2ecd7-117">Obiekt wywołujący nie jest wykonywany w apartamentie.</span><span class="sxs-lookup"><span data-stu-id="2ecd7-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2ecd7-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ecd7-118">Remarks</span></span>

<span data-ttu-id="2ecd7-119">Ta funkcja otacza wywołanie metody [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="2ecd7-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ecd7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ecd7-120">Requirements</span></span>  
 <span data-ttu-id="2ecd7-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ecd7-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ecd7-122">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="2ecd7-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2ecd7-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2ecd7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ecd7-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ecd7-124">See also</span></span>

- [<span data-ttu-id="2ecd7-125">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="2ecd7-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
