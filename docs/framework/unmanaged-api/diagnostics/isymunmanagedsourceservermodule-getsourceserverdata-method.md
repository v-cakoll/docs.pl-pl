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
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176581"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="a5631-102">ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda</span><span class="sxs-lookup"><span data-stu-id="a5631-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="a5631-103">Zwraca dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="a5631-103">Returns the source server data for the module.</span></span> <span data-ttu-id="a5631-104">Rozmówca musi zwolnić zasoby `CoTaskMemFree`za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="a5631-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5631-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5631-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5631-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5631-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="a5631-107">[na zewnątrz] Wskaźnik `ULONG32` do, który odbiera rozmiar w bajtach danych serwera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a5631-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a5631-108">[na zewnątrz] Wskaźnik do zwróconej `pDataByteCount` wartości.</span><span class="sxs-lookup"><span data-stu-id="a5631-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5631-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5631-109">Return Value</span></span>  
 <span data-ttu-id="a5631-110">S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a5631-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5631-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5631-111">Requirements</span></span>  
 <span data-ttu-id="a5631-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a5631-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5631-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5631-113">See also</span></span>

- [<span data-ttu-id="a5631-114">ISymUnmanagedSourceServerModule — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a5631-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
