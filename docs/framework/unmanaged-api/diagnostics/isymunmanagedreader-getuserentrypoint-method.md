---
title: ISymUnmanagedReader::GetUserEntryPoint — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
ms.openlocfilehash: d465f830fa73016c3cf3f7df3a4a4d0c42bc0980
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615504"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="b261c-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="b261c-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="b261c-103">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="b261c-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="b261c-104">Na przykład ta metoda może być główną metodą użytkownika, a nie wygenerowanymi przez kompilator wycinkami przed metodą Main.</span><span class="sxs-lookup"><span data-stu-id="b261c-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b261c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b261c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b261c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b261c-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="b261c-107">określoną Wskaźnik do zmiennej, która otrzymuje punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="b261c-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b261c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b261c-108">Return Value</span></span>  
 <span data-ttu-id="b261c-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b261c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b261c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b261c-110">Requirements</span></span>  
 <span data-ttu-id="b261c-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b261c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b261c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b261c-112">See also</span></span>

- [<span data-ttu-id="b261c-113">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b261c-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
