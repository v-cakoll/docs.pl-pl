---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614581"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="0dc74-102">ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="0dc74-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="0dc74-103">Pobiera liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0dc74-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0dc74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dc74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0dc74-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="0dc74-106">podczas Token metadanych metod.</span><span class="sxs-lookup"><span data-stu-id="0dc74-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="0dc74-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania liczby zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0dc74-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dc74-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0dc74-108">Return Value</span></span>  
 <span data-ttu-id="0dc74-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0dc74-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc74-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0dc74-110">Requirements</span></span>  
 <span data-ttu-id="0dc74-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0dc74-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc74-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dc74-112">See also</span></span>

- [<span data-ttu-id="0dc74-113">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="0dc74-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
