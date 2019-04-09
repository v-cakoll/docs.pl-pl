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
ms.openlocfilehash: d4bc763d908156f3bbf8998c13073820686903f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132759"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="7094a-102">ISymUnmanagedReader::GetMethodByVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="7094a-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="7094a-103">Pobiera metodę czytnika symboli podany token metody i numeru wersji edycji i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7094a-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="7094a-104">Numery wersji są liczone od 1 i są zwiększane, każdym razem, gdy metoda zostanie zmieniony w wyniku operacji Edytuj i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7094a-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7094a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7094a-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7094a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7094a-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="7094a-107">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="7094a-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="7094a-108">[in] Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="7094a-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="7094a-109">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7094a-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7094a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7094a-110">Return Value</span></span>  
 <span data-ttu-id="7094a-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="7094a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7094a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7094a-112">Requirements</span></span>  
 <span data-ttu-id="7094a-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7094a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7094a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7094a-114">See also</span></span>

- [<span data-ttu-id="7094a-115">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7094a-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
