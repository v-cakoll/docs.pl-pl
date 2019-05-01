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
ms.openlocfilehash: a4d15d9ae63e63f98ab73e250df558dfa16002a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959968"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="27a10-102">ICorDebugFunction2::EnumerateNativeCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="27a10-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="27a10-103">Pobiera wskaźnik interfejsu do icordebugcodeenum — obiekt, który zawiera instrukcje kodu natywnego w funkcji odwołuje się ten obiekt icordebugfunction2 —.</span><span class="sxs-lookup"><span data-stu-id="27a10-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27a10-104">`EnumerateNativeCode` nie jest zaimplementowana w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27a10-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27a10-105">Syntax</span></span>  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="27a10-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27a10-106">Requirements</span></span>  
 <span data-ttu-id="27a10-107">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27a10-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
