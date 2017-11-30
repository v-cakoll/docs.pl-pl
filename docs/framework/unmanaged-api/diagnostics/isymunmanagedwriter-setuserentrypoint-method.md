---
title: "ISymUnmanagedWriter::SetUserEntryPoint — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be7f348237fdcf0a136d34ce3b6b8548c16d5547
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="e45b1-102">ISymUnmanagedWriter::SetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="e45b1-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="e45b1-103">Określa metodę zdefiniowane przez użytkownika, który jest punkt wejścia dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="e45b1-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="e45b1-104">Ten punkt wejścia można na przykład metoda głównego użytkownika zamiast generowane przez kompilator klas zastępczych przed funkcją main.</span><span class="sxs-lookup"><span data-stu-id="e45b1-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45b1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e45b1-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e45b1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e45b1-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="e45b1-107">[in] Token metadanych metodę, która jest wpisu użytkownika punktu.</span><span class="sxs-lookup"><span data-stu-id="e45b1-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e45b1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e45b1-108">Return Value</span></span>  
 <span data-ttu-id="e45b1-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e45b1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e45b1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e45b1-110">Requirements</span></span>  
 <span data-ttu-id="e45b1-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e45b1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45b1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e45b1-112">See Also</span></span>  
 [<span data-ttu-id="e45b1-113">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="e45b1-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
