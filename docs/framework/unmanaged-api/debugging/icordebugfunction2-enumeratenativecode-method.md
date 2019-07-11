---
title: ICorDebugFunction2::EnumerateNativeCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61dcf014a65f524d2b2e7b92bcc7f007d1a47125
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754502"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="52991-102">ICorDebugFunction2::EnumerateNativeCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="52991-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="52991-103">Pobiera wskaźnik interfejsu do icordebugcodeenum — obiekt, który zawiera instrukcje kodu natywnego w funkcji odwołuje się ten obiekt icordebugfunction2 —.</span><span class="sxs-lookup"><span data-stu-id="52991-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52991-104">`EnumerateNativeCode` nie jest zaimplementowana w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52991-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52991-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="52991-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="52991-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52991-106">Requirements</span></span>  
 <span data-ttu-id="52991-107">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52991-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
