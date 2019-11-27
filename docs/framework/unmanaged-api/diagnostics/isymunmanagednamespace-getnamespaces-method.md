---
title: ISymUnmanagedNamespace::GetNamespaces — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: da2906187c02bbc7a35c937663e3fc7db1ebda13
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433887"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="fc7bf-102">ISymUnmanagedNamespace::GetNamespaces — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc7bf-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="fc7bf-103">Pobiera elementy podrzędne tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fc7bf-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc7bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc7bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc7bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc7bf-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="fc7bf-106">podczas `ULONG32`, który wskazuje rozmiar tablicy `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="fc7bf-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="fc7bf-107">określoną Wskaźnik do `ULONG32`, który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fc7bf-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="fc7bf-108">określoną Wskaźnik do buforu, który zawiera przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="fc7bf-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc7bf-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="fc7bf-109">Return Value</span></span>  
 <span data-ttu-id="fc7bf-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fc7bf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc7bf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc7bf-111">Requirements</span></span>  
 <span data-ttu-id="fc7bf-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fc7bf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7bf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc7bf-113">See also</span></span>

- [<span data-ttu-id="fc7bf-114">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc7bf-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
