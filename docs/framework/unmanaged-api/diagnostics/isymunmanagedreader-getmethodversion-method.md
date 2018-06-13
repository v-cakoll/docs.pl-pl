---
title: ISymUnmanagedReader::GetMethodVersion — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d850363940ff53135fc66ec057ee67822fa40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424667"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="9d718-102">ISymUnmanagedReader::GetMethodVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d718-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="9d718-103">Pobiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="9d718-103">Gets the method version.</span></span> <span data-ttu-id="9d718-104">Wersja metody rozpoczyna się od 1 i jest zwiększany zawsze, gdy metoda jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="9d718-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="9d718-105">Ponowna kompilacja może się zdarzyć bez wprowadzania zmian do metody.</span><span class="sxs-lookup"><span data-stu-id="9d718-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d718-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d718-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d718-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d718-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="9d718-108">[in] Metoda, dla którego można pobrać wersji.</span><span class="sxs-lookup"><span data-stu-id="9d718-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="9d718-109">[out] Wskaźnik do zmiennej, która odbiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="9d718-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d718-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d718-110">Return Value</span></span>  
 <span data-ttu-id="9d718-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9d718-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d718-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d718-112">Requirements</span></span>  
 <span data-ttu-id="9d718-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9d718-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d718-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d718-114">See Also</span></span>  
 [<span data-ttu-id="9d718-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d718-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
