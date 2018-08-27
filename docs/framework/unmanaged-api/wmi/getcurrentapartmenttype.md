---
title: Funkcja GetCurrentApartmentType (niezarządzany wykaz interfejsów API)
description: Funkcja GetCurrentApartmentType pobiera typu apartment, w którym jest wykonywany obiekt wywołujący.
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
ms.openlocfilehash: 4de85eb310de70dc8fd61f7c06abca95ec267f87
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931418"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="a1de8-103">GetCurrentApartmentType — funkcja</span><span class="sxs-lookup"><span data-stu-id="a1de8-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="a1de8-104">Pobiera rodzaj typu apartment, w którym jest wykonywany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a1de8-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a1de8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1de8-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="a1de8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1de8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a1de8-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="a1de8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a1de8-108">[in] Wskaźnik do [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1de8-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="a1de8-109">[out] Wskaźnik do [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) wartość wyliczenia wskazująca apartamentu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a1de8-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="a1de8-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1de8-110">Return value</span></span>


|<span data-ttu-id="a1de8-111">Stała</span><span class="sxs-lookup"><span data-stu-id="a1de8-111">Constant</span></span>  |<span data-ttu-id="a1de8-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="a1de8-112">Value</span></span>  |<span data-ttu-id="a1de8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a1de8-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="a1de8-114">0</span><span class="sxs-lookup"><span data-stu-id="a1de8-114">0</span></span> | <span data-ttu-id="a1de8-115">Funkcja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1de8-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="a1de8-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="a1de8-116">0x80000008</span></span> | <span data-ttu-id="a1de8-117">Obiekt wywołujący nie jest wykonywana w komórce.</span><span class="sxs-lookup"><span data-stu-id="a1de8-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a1de8-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1de8-118">Remarks</span></span>

<span data-ttu-id="a1de8-119">Ta funkcja zawija wywołanie do [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.</span><span class="sxs-lookup"><span data-stu-id="a1de8-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1de8-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1de8-120">Requirements</span></span>  
 <span data-ttu-id="a1de8-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1de8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1de8-122">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a1de8-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a1de8-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a1de8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1de8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1de8-124">See also</span></span>  
[<span data-ttu-id="a1de8-125">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="a1de8-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
