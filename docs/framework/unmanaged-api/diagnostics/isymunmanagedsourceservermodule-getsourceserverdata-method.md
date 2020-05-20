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
ms.openlocfilehash: 9a3a6c07a9cace0ac9834cdb05925a301285204c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615322"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="3f352-102">ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f352-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="3f352-103">Zwraca dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="3f352-103">Returns the source server data for the module.</span></span> <span data-ttu-id="3f352-104">Obiekt wywołujący musi zwolnić zasoby za pomocą polecenia `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="3f352-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f352-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f352-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f352-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f352-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="3f352-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w bajtach) danych serwera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3f352-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="3f352-108">określoną Wskaźnik do zwracanej `pDataByteCount` wartości.</span><span class="sxs-lookup"><span data-stu-id="3f352-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f352-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3f352-109">Return Value</span></span>  
 <span data-ttu-id="3f352-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3f352-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f352-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f352-111">Requirements</span></span>  
 <span data-ttu-id="3f352-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3f352-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f352-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f352-113">See also</span></span>

- [<span data-ttu-id="3f352-114">ISymUnmanagedSourceServerModule — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f352-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
