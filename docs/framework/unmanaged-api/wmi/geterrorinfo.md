---
title: GetErrorInfo — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcja GetErrorInfo pobiera informacje o błędzie z poprzedniego wywołania funkcji.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef52a4e503597e08eae407571f02bf63adafc4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455961"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="193ea-103">GetErrorInfo — funkcja</span><span class="sxs-lookup"><span data-stu-id="193ea-103">GetErrorInfo function</span></span>
<span data-ttu-id="193ea-104">Pobiera informacje o błędzie z poprzedniego wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="193ea-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="193ea-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="193ea-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="193ea-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="193ea-106">Return value</span></span>

<span data-ttu-id="193ea-107">Wskaźnik do [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) obiektu, jeśli wywołanie funkcji zakończy się pomyślnie, lub `null` w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="193ea-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="193ea-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="193ea-108">Remarks</span></span>

<span data-ttu-id="193ea-109">Ta funkcja jest zawijana wywołanie [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="193ea-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="193ea-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="193ea-110">Requirements</span></span>  
 <span data-ttu-id="193ea-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="193ea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="193ea-112">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="193ea-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="193ea-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="193ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193ea-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="193ea-114">See also</span></span>  
[<span data-ttu-id="193ea-115">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="193ea-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
