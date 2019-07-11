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
ms.openlocfilehash: 3f45423bb0ff4c755e657729c5725c8d9a22bde3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746766"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="68dbb-102">ISymUnmanagedReader::GetMethodVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="68dbb-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="68dbb-103">Pobiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="68dbb-103">Gets the method version.</span></span> <span data-ttu-id="68dbb-104">Wersja metody rozpoczyna się od 1 i rośnie, każdym razem, gdy metoda jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="68dbb-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="68dbb-105">Ponowna kompilacja może się zdarzyć bez konieczności wprowadzania zmian do metody.</span><span class="sxs-lookup"><span data-stu-id="68dbb-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68dbb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="68dbb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68dbb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="68dbb-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="68dbb-108">[in] Metoda, dla którego można pobrać wersji.</span><span class="sxs-lookup"><span data-stu-id="68dbb-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="68dbb-109">[out] Wskaźnik do zmiennej, która odbiera wersji metody.</span><span class="sxs-lookup"><span data-stu-id="68dbb-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68dbb-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="68dbb-110">Return Value</span></span>  
 <span data-ttu-id="68dbb-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="68dbb-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68dbb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68dbb-112">Requirements</span></span>  
 <span data-ttu-id="68dbb-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="68dbb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dbb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68dbb-114">See also</span></span>

- [<span data-ttu-id="68dbb-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="68dbb-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
