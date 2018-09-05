---
title: Funkcja QualifierSet_EndEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_EndEnumeration kończy wyliczenia.
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
ms.openlocfilehash: dbf47dbfddac7d48b78c9d52969de1ef03385c15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524317"
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="fdea1-103">QualifierSet_EndEnumeration — funkcja</span><span class="sxs-lookup"><span data-stu-id="fdea1-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="fdea1-104">Kończy wyliczenie uruchomione z wywołaniem [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="fdea1-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fdea1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdea1-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="fdea1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdea1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fdea1-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="fdea1-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="fdea1-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdea1-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="fdea1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fdea1-109">Return value</span></span>

<span data-ttu-id="fdea1-110">Następującą wartość zwrócona przez tę funkcję jest zdefiniowany w *WbemCli.h* pliku nagłówka, lub można zdefiniować ją jako stała w kodzie:</span><span class="sxs-lookup"><span data-stu-id="fdea1-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="fdea1-111">Stała</span><span class="sxs-lookup"><span data-stu-id="fdea1-111">Constant</span></span>  |<span data-ttu-id="fdea1-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="fdea1-112">Value</span></span>  |<span data-ttu-id="fdea1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fdea1-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fdea1-114">0</span><span class="sxs-lookup"><span data-stu-id="fdea1-114">0</span></span> | <span data-ttu-id="fdea1-115">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fdea1-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fdea1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdea1-116">Remarks</span></span>

<span data-ttu-id="fdea1-117">Ta funkcja zawija wywołanie do [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="fdea1-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="fdea1-118">To wywołanie jest zalecane, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="fdea1-118">This call is recommended, but not required.</span></span> <span data-ttu-id="fdea1-119">Go natychmiast zwalnia zasoby skojarzone z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fdea1-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="fdea1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdea1-120">Requirements</span></span>  

<span data-ttu-id="fdea1-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdea1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="fdea1-122">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fdea1-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="fdea1-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fdea1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdea1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdea1-124">See also</span></span>  
[<span data-ttu-id="fdea1-125">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="fdea1-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
