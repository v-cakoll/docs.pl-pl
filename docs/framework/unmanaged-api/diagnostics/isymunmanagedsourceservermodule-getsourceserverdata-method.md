---
title: ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e83a5ff489881938c1e8410f765fd63f3b5d84
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479444"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="f9062-102">ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9062-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="f9062-103">Zwraca dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="f9062-103">Returns the source server data for the module.</span></span> <span data-ttu-id="f9062-104">Obiekt wywołujący musi zwolnić zasoby przy użyciu `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="f9062-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9062-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9062-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9062-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9062-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="f9062-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar w bajtach, danych serwera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f9062-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="f9062-108">[out] Wskaźnik do zwracanego `pDataByteCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="f9062-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9062-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f9062-109">Return Value</span></span>  
 <span data-ttu-id="f9062-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="f9062-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9062-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9062-111">Requirements</span></span>  
 <span data-ttu-id="f9062-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9062-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9062-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9062-113">See also</span></span>
- [<span data-ttu-id="f9062-114">ISymUnmanagedSourceServerModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9062-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
