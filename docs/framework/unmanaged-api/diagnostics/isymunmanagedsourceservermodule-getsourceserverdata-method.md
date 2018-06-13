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
ms.openlocfilehash: afc041896615e906ac49eed9a7be139dff217463
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427014"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="9026f-102">ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda</span><span class="sxs-lookup"><span data-stu-id="9026f-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="9026f-103">Zwraca dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="9026f-103">Returns the source server data for the module.</span></span> <span data-ttu-id="9026f-104">Obiekt wywołujący musi zwolnić zasoby przy użyciu `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="9026f-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9026f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9026f-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9026f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9026f-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="9026f-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar w bajtach, źródła danych serwera.</span><span class="sxs-lookup"><span data-stu-id="9026f-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="9026f-108">[out] Wskaźnik do zwróconego `pDataByteCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="9026f-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9026f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9026f-109">Return Value</span></span>  
 <span data-ttu-id="9026f-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9026f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9026f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9026f-111">Requirements</span></span>  
 <span data-ttu-id="9026f-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9026f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9026f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9026f-113">See Also</span></span>  
 [<span data-ttu-id="9026f-114">ISymUnmanagedSourceServerModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="9026f-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
