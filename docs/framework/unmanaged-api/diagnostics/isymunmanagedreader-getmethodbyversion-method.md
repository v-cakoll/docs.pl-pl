---
title: "ISymUnmanagedReader::GetMethodByVersion — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodByVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba4c3ae5b1883c3113d205eab44375cbd1034c29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="dbbc1-102">ISymUnmanagedReader::GetMethodByVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="dbbc1-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="dbbc1-103">Pobiera metodę czytnika symboli podany token metody i numer wersji edycji i kopii.</span><span class="sxs-lookup"><span data-stu-id="dbbc1-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="dbbc1-104">Numery wersji są liczone od 1 i są zwiększany po każdej zmianie metody wyniku operacji Edytuj i kopii.</span><span class="sxs-lookup"><span data-stu-id="dbbc1-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbc1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbbc1-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbbc1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbbc1-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="dbbc1-107">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="dbbc1-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="dbbc1-108">[in] Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="dbbc1-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="dbbc1-109">[out] Wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="dbbc1-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbbc1-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dbbc1-110">Return Value</span></span>  
 <span data-ttu-id="dbbc1-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="dbbc1-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbbc1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbbc1-112">Requirements</span></span>  
 <span data-ttu-id="dbbc1-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dbbc1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbc1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbbc1-114">See Also</span></span>  
 [<span data-ttu-id="dbbc1-115">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="dbbc1-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
