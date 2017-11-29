---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f3c00f3a0efd41c425ba29f8465a73e78d624c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="e5558-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="e5558-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="e5558-103">Tworzy inny moduł wyliczający raw urządzenia wejściowego z takim samym stanie, aby jako bieżącego modułu wyliczającego, aby przejść przez tę samą listę.</span><span class="sxs-lookup"><span data-stu-id="e5558-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5558-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5558-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5558-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5558-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="e5558-106">[out] Adresu zmiennej danych wyjściowych, który odbiera [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e5558-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="e5558-107">Jeśli metoda zakończy się niepowodzeniem, wartość tej zmiennej danych wyjściowych jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="e5558-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e5558-108">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="e5558-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="e5558-109">Wynik HRESULT: Ta metoda obsługuje standardowe wartości zwracanych E_INVALIDARG E_OUTOFMEMORY i E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="e5558-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5558-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5558-110">Remarks</span></span>  
 <span data-ttu-id="e5558-111">Ta metoda umożliwia rejestrowanie punktu w sekwencji wyliczenie aby powrócić do tego punktu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="e5558-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="e5558-112">Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający niezależnie od pierwszego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="e5558-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
