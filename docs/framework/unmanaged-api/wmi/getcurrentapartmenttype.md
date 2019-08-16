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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68eb4ba653098d847022da45e610cb4fa5496a8c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037963"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="b565a-103">GetCurrentApartmentType, funkcja</span><span class="sxs-lookup"><span data-stu-id="b565a-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="b565a-104">Pobiera typ apartamentu, w którym wykonywany jest obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="b565a-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b565a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b565a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="b565a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b565a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b565a-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="b565a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b565a-108">podczas Wskaźnik do wystąpienia [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .</span><span class="sxs-lookup"><span data-stu-id="b565a-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="b565a-109">określoną Wskaźnik do [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) wartości wyliczenia, który wskazuje Apartament obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b565a-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="b565a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b565a-110">Return value</span></span>

|<span data-ttu-id="b565a-111">Stała</span><span class="sxs-lookup"><span data-stu-id="b565a-111">Constant</span></span>  |<span data-ttu-id="b565a-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="b565a-112">Value</span></span>  |<span data-ttu-id="b565a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b565a-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="b565a-114">0</span><span class="sxs-lookup"><span data-stu-id="b565a-114">0</span></span> | <span data-ttu-id="b565a-115">Funkcja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b565a-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="b565a-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="b565a-116">0x80000008</span></span> | <span data-ttu-id="b565a-117">Obiekt wywołujący nie jest wykonywany w apartamentie.</span><span class="sxs-lookup"><span data-stu-id="b565a-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="b565a-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b565a-118">Remarks</span></span>

<span data-ttu-id="b565a-119">Ta funkcja otacza wywołanie metody [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="b565a-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b565a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b565a-120">Requirements</span></span>  
 <span data-ttu-id="b565a-121">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b565a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b565a-122">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b565a-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b565a-123">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b565a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b565a-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b565a-124">See also</span></span>

- [<span data-ttu-id="b565a-125">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="b565a-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
