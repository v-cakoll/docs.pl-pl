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
ms.openlocfilehash: f4b51fe4510f4172227d9afd049eb6815790a165
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783086"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="c020d-103">VerifyClientKey — funkcja</span><span class="sxs-lookup"><span data-stu-id="c020d-103">VerifyClientKey function</span></span>
<span data-ttu-id="c020d-104">Zapewnia, że klucz klienta ma poprawne zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c020d-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c020d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c020d-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="c020d-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c020d-106">Return value</span></span>

<span data-ttu-id="c020d-107">Jeśli funkcja się powiedzie, wartość zwracana jest `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="c020d-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="c020d-108">Jeśli funkcja zawiedzie, wartością zwracaną jest kod błędu różny od zera, zdefiniowany w *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="c020d-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="c020d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c020d-109">Requirements</span></span>  
 <span data-ttu-id="c020d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c020d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c020d-111">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="c020d-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="c020d-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c020d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c020d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c020d-113">See also</span></span>

- [<span data-ttu-id="c020d-114">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="c020d-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
