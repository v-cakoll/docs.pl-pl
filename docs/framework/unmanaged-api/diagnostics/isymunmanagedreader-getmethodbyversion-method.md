---
title: ISymUnmanagedReader::GetMethodByVersion — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3210f0186401729a5bc95369e88b290ae49a634
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776993"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="dc9fa-102">ISymUnmanagedReader::GetMethodByVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc9fa-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="dc9fa-103">Pobiera metodę czytnika symboli podany token metody i numeru wersji edycji i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="dc9fa-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="dc9fa-104">Numery wersji są liczone od 1 i są zwiększane, każdym razem, gdy metoda zostanie zmieniony w wyniku operacji Edytuj i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="dc9fa-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9fa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc9fa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc9fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc9fa-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="dc9fa-107">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="dc9fa-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="dc9fa-108">[in] Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="dc9fa-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="dc9fa-109">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="dc9fa-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc9fa-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc9fa-110">Return Value</span></span>  
 <span data-ttu-id="dc9fa-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="dc9fa-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9fa-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc9fa-112">Requirements</span></span>  
 <span data-ttu-id="dc9fa-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dc9fa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9fa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc9fa-114">See also</span></span>

- [<span data-ttu-id="dc9fa-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc9fa-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
