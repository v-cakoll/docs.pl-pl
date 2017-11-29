---
title: "ISymUnmanagedScope::GetEndOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dd3b7c78c3a43109c3508487aa34650f0f16d196
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="05d8a-102">ISymUnmanagedScope::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="05d8a-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="05d8a-103">Pobiera przesunięcie zakończenia dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="05d8a-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05d8a-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05d8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05d8a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="05d8a-106">[out] Wskaźnik do `ULONG32` odbierająca przesunięcie zakończenia.</span><span class="sxs-lookup"><span data-stu-id="05d8a-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05d8a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05d8a-107">Return Value</span></span>  
 <span data-ttu-id="05d8a-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="05d8a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d8a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05d8a-109">Requirements</span></span>  
 <span data-ttu-id="05d8a-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="05d8a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d8a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05d8a-111">See Also</span></span>  
 [<span data-ttu-id="05d8a-112">ISymUnmanagedScope — interfejs</span><span class="sxs-lookup"><span data-stu-id="05d8a-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="05d8a-113">GetStartOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="05d8a-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
