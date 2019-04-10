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
ms.openlocfilehash: 47fee26a0c4c25e4bff5bca94e5e26daaf98cccd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214718"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="3bbdc-103">VerifyClientKey — funkcja</span><span class="sxs-lookup"><span data-stu-id="3bbdc-103">VerifyClientKey function</span></span>
<span data-ttu-id="3bbdc-104">Zapewnia, że klucz klienta ma poprawne zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3bbdc-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3bbdc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bbdc-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="3bbdc-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3bbdc-106">Return value</span></span>

<span data-ttu-id="3bbdc-107">Jeśli funkcja się powiedzie, wartość zwracana jest `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="3bbdc-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="3bbdc-108">Jeśli funkcja zawiedzie, wartością zwracaną jest kod błędu różny od zera, zdefiniowany w *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="3bbdc-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="3bbdc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bbdc-109">Requirements</span></span>  
 <span data-ttu-id="3bbdc-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bbdc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bbdc-111">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="3bbdc-111">**Header:** WMINet_Utils.def</span></span>  
  
 **<span data-ttu-id="3bbdc-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3bbdc-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3bbdc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bbdc-113">See also</span></span>

- [<span data-ttu-id="3bbdc-114">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="3bbdc-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
