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
ms.openlocfilehash: a6a6aa937078ed0627688a4eed3d9142a2e6e0ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428103"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="bc24e-102">ISymUnmanagedWriter::CloseMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc24e-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="bc24e-103">Zamyka bieżącą metodę.</span><span class="sxs-lookup"><span data-stu-id="bc24e-103">Closes the current method.</span></span> <span data-ttu-id="bc24e-104">Po zamknięciu metody nie można definiować więcej symboli.</span><span class="sxs-lookup"><span data-stu-id="bc24e-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc24e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc24e-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bc24e-106">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="bc24e-106">Return Value</span></span>  
 <span data-ttu-id="bc24e-107">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bc24e-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc24e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc24e-108">Requirements</span></span>  
 <span data-ttu-id="bc24e-109">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bc24e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc24e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc24e-110">See also</span></span>

- [<span data-ttu-id="bc24e-111">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc24e-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="bc24e-112">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="bc24e-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
