---
title: Funkcja VerifyClientKey (niezarządzany wykaz interfejsów API)
description: Funkcja VerifyClientKey gwarantuje, że klucz klienta ma poprawne zabezpieczenia.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94d601125049f0c215b3b03bf8b13d2959872c3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711762"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="cc4e9-103">VerifyClientKey — funkcja</span><span class="sxs-lookup"><span data-stu-id="cc4e9-103">VerifyClientKey function</span></span>
<span data-ttu-id="cc4e9-104">Zapewnia, że klucz klienta ma poprawne zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cc4e9-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="cc4e9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc4e9-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="cc4e9-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc4e9-106">Return value</span></span>

<span data-ttu-id="cc4e9-107">Jeśli funkcja się powiedzie, wartość zwracana jest `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="cc4e9-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="cc4e9-108">Jeśli funkcja zawiedzie, wartością zwracaną jest kod błędu różny od zera, zdefiniowany w *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="cc4e9-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc4e9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc4e9-109">Requirements</span></span>  
 <span data-ttu-id="cc4e9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc4e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4e9-111">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="cc4e9-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="cc4e9-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cc4e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4e9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc4e9-113">See also</span></span>
- [<span data-ttu-id="cc4e9-114">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="cc4e9-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
