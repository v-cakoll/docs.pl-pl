---
title: "Funkcja GetCurrentApartmentType (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetCurrentApartmentType pobiera typu Apartment, w którym jest wykonywany wywołującego."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b250913b55ba59261a666760cc15466b6f9d096e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="7deba-103">Funkcja GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="7deba-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="7deba-104">Pobiera rodzaj typu apartment, w którym jest wykonywany wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7deba-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7deba-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7deba-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="7deba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7deba-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7deba-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="7deba-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7deba-108">[in] Wskaźnik do [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7deba-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="7deba-109">[out] Wskaźnik do [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) wartość wyliczenia wskazująca apartamentu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7deba-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="7deba-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7deba-110">Return value</span></span>


|<span data-ttu-id="7deba-111">Stała</span><span class="sxs-lookup"><span data-stu-id="7deba-111">Constant</span></span>  |<span data-ttu-id="7deba-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="7deba-112">Value</span></span>  |<span data-ttu-id="7deba-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7deba-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="7deba-114">0</span><span class="sxs-lookup"><span data-stu-id="7deba-114">0</span></span> | <span data-ttu-id="7deba-115">Funkcja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7deba-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="7deba-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="7deba-116">0x80000008</span></span> | <span data-ttu-id="7deba-117">Obiekt wywołujący nie jest wykonywana w komórce.</span><span class="sxs-lookup"><span data-stu-id="7deba-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7deba-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7deba-118">Remarks</span></span>

<span data-ttu-id="7deba-119">Ta funkcja jest zawijana wywołanie [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="7deba-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7deba-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7deba-120">Requirements</span></span>  
 <span data-ttu-id="7deba-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7deba-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7deba-122">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7deba-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7deba-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7deba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7deba-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7deba-124">See also</span></span>  
[<span data-ttu-id="7deba-125">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="7deba-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
