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
ms.openlocfilehash: 591279a80b7d6a770127fb98eb71c056c48bdffd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231217"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="44862-102">ISymUnmanagedWriter::CloseMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="44862-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="44862-103">Zamyka bieżącą metodę.</span><span class="sxs-lookup"><span data-stu-id="44862-103">Closes the current method.</span></span> <span data-ttu-id="44862-104">Po zamknięciu metody żadnych więcej symboli można zdefiniować w nim.</span><span class="sxs-lookup"><span data-stu-id="44862-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44862-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="44862-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="44862-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44862-106">Return Value</span></span>  
 <span data-ttu-id="44862-107">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="44862-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44862-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44862-108">Requirements</span></span>  
 <span data-ttu-id="44862-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="44862-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44862-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44862-110">See also</span></span>

- [<span data-ttu-id="44862-111">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="44862-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="44862-112">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="44862-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
