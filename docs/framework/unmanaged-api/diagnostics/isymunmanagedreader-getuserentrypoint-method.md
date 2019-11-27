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
ms.openlocfilehash: 50f41bb55b7c3dc45646a465032074ce90be0abf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444505"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="b79fb-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="b79fb-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="b79fb-103">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="b79fb-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="b79fb-104">Na przykład ta metoda może być główną metodą użytkownika, a nie wygenerowanymi przez kompilator wycinkami przed metodą Main.</span><span class="sxs-lookup"><span data-stu-id="b79fb-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79fb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b79fb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b79fb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b79fb-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="b79fb-107">określoną Wskaźnik do zmiennej, która otrzymuje punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="b79fb-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b79fb-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="b79fb-108">Return Value</span></span>  
 <span data-ttu-id="b79fb-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b79fb-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b79fb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b79fb-110">Requirements</span></span>  
 <span data-ttu-id="b79fb-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b79fb-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79fb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b79fb-112">See also</span></span>

- [<span data-ttu-id="b79fb-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="b79fb-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
