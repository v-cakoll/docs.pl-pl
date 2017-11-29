---
title: "ISymUnmanagedReader::GetMethodVersion — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b57407cb12e4315b6a144d157a201f857614d9f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="24f92-102">ISymUnmanagedReader::GetMethodVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="24f92-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="24f92-103">Pobiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="24f92-103">Gets the method version.</span></span> <span data-ttu-id="24f92-104">Wersja metody rozpoczyna się od 1 i jest zwiększany zawsze, gdy metoda jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="24f92-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="24f92-105">Ponowna kompilacja może się zdarzyć bez wprowadzania zmian do metody.</span><span class="sxs-lookup"><span data-stu-id="24f92-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f92-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="24f92-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24f92-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="24f92-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="24f92-108">[in] Metoda, dla którego można pobrać wersji.</span><span class="sxs-lookup"><span data-stu-id="24f92-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="24f92-109">[out] Wskaźnik do zmiennej, która odbiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="24f92-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24f92-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24f92-110">Return Value</span></span>  
 <span data-ttu-id="24f92-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="24f92-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f92-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24f92-112">Requirements</span></span>  
 <span data-ttu-id="24f92-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="24f92-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f92-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24f92-114">See Also</span></span>  
 [<span data-ttu-id="24f92-115">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="24f92-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
