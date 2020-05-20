---
title: ISymUnmanagedScope::GetNamespaces — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
ms.openlocfilehash: 6f11a69671864ba4627c2bb8c86e0c9beb27eeb1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611123"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="32dd0-102">ISymUnmanagedScope::GetNamespaces — Metoda</span><span class="sxs-lookup"><span data-stu-id="32dd0-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="32dd0-103">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="32dd0-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32dd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32dd0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32dd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32dd0-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="32dd0-106">podczas Rozmiar `namespaces` tablicy.</span><span class="sxs-lookup"><span data-stu-id="32dd0-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="32dd0-107">określoną Wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu wymaganego do przechowywania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32dd0-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="32dd0-108">określoną Tablica, która odbiera przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="32dd0-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32dd0-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32dd0-109">Return Value</span></span>  
 <span data-ttu-id="32dd0-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="32dd0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32dd0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32dd0-111">Requirements</span></span>  
 <span data-ttu-id="32dd0-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="32dd0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32dd0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32dd0-113">See also</span></span>

- [<span data-ttu-id="32dd0-114">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="32dd0-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
