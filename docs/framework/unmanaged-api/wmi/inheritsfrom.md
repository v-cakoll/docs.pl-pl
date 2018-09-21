---
title: Funkcja InheritsFrom (niezarządzany wykaz interfejsów API)
description: Funkcja InheritsFrom Określa, czy klasy lub wystąpienia pochodzi z klasy nadrzędnej określonej.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4784e22d5a3eec031fbee00441958a62d66b52df
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46477786"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="acb3d-103">InheritsFrom — funkcja</span><span class="sxs-lookup"><span data-stu-id="acb3d-103">InheritsFrom function</span></span>
<span data-ttu-id="acb3d-104">Określa, czy bieżącą klasę lub wystąpienie dziedziczy po określonej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="acb3d-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="acb3d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="acb3d-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="acb3d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="acb3d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="acb3d-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="acb3d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="acb3d-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="acb3d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="acb3d-109">[in] Nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="acb3d-109">[in] The name of the class.</span></span> <span data-ttu-id="acb3d-110">`wszAncestor` musi wskazywać prawidłowy `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="acb3d-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="acb3d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="acb3d-111">Return value</span></span>

<span data-ttu-id="acb3d-112">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="acb3d-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="acb3d-113">Stała</span><span class="sxs-lookup"><span data-stu-id="acb3d-113">Constant</span></span>  |<span data-ttu-id="acb3d-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="acb3d-114">Value</span></span>  |<span data-ttu-id="acb3d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="acb3d-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="acb3d-116">0</span><span class="sxs-lookup"><span data-stu-id="acb3d-116">0</span></span> | <span data-ttu-id="acb3d-117">Bieżący obiekt dziedziczy `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="acb3d-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="acb3d-118">1</span><span class="sxs-lookup"><span data-stu-id="acb3d-118">1</span></span> | <span data-ttu-id="acb3d-119">Bieżący obiekt nie dziedziczy `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="acb3d-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="acb3d-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="acb3d-120">0x80041008</span></span> | <span data-ttu-id="acb3d-121">`wszAncestor` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="acb3d-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="acb3d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acb3d-122">Remarks</span></span>

<span data-ttu-id="acb3d-123">Ta funkcja zawija wywołanie do [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) metody.</span><span class="sxs-lookup"><span data-stu-id="acb3d-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="acb3d-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="acb3d-124">Requirements</span></span>  
 <span data-ttu-id="acb3d-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb3d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb3d-126">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="acb3d-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="acb3d-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="acb3d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb3d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acb3d-128">See also</span></span>  
[<span data-ttu-id="acb3d-129">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="acb3d-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
