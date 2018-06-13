---
title: ISymUnmanagedWriter::CloseMethod — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71be697a8a1decd9b5f780d047c3dbb397e351d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426894"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="7979d-102">ISymUnmanagedWriter::CloseMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="7979d-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="7979d-103">Zamyka bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="7979d-103">Closes the current method.</span></span> <span data-ttu-id="7979d-104">Po zamknięciu metody nie więcej symboli można zdefiniować w niej.</span><span class="sxs-lookup"><span data-stu-id="7979d-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7979d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7979d-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7979d-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7979d-106">Return Value</span></span>  
 <span data-ttu-id="7979d-107">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7979d-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7979d-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7979d-108">Requirements</span></span>  
 <span data-ttu-id="7979d-109">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7979d-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7979d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7979d-110">See Also</span></span>  
 [<span data-ttu-id="7979d-111">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7979d-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="7979d-112">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="7979d-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
