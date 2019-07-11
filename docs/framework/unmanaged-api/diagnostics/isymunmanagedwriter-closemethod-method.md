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
ms.openlocfilehash: 23f77f30b84622dffd8c76bb9302ad564f40ed41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778189"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="98b7c-102">ISymUnmanagedWriter::CloseMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="98b7c-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="98b7c-103">Zamyka bieżącą metodę.</span><span class="sxs-lookup"><span data-stu-id="98b7c-103">Closes the current method.</span></span> <span data-ttu-id="98b7c-104">Po zamknięciu metody żadnych więcej symboli można zdefiniować w nim.</span><span class="sxs-lookup"><span data-stu-id="98b7c-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b7c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="98b7c-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="98b7c-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="98b7c-106">Return Value</span></span>  
 <span data-ttu-id="98b7c-107">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="98b7c-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98b7c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98b7c-108">Requirements</span></span>  
 <span data-ttu-id="98b7c-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="98b7c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b7c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98b7c-110">See also</span></span>

- [<span data-ttu-id="98b7c-111">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="98b7c-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="98b7c-112">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="98b7c-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
