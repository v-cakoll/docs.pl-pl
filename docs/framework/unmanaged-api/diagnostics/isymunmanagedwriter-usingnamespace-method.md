---
title: "ISymUnmanagedWriter::UsingNamespace — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.UsingNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9bfd5ca0c22a9b4da1acb1f93b29150beba865a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="aaf2a-102">ISymUnmanagedWriter::UsingNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="aaf2a-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="aaf2a-103">Określa, że podana nazwa przestrzeni nazw FQDN jest w użyciu w zakresie leksykalne aktualnie otwarte.</span><span class="sxs-lookup"><span data-stu-id="aaf2a-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="aaf2a-104">Przestrzeń nazw będzie używany w ramach wszystkie zakresy, które dziedziczą po zakresie aktualnie otwarte.</span><span class="sxs-lookup"><span data-stu-id="aaf2a-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="aaf2a-105">Zamykanie bieżącego zakresu spowoduje również przerwanie Użyj przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="aaf2a-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf2a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaf2a-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aaf2a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaf2a-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="aaf2a-108">[in] Wskaźnik do w pełni kwalifikowana nazwa przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="aaf2a-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf2a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aaf2a-109">Return Value</span></span>  
 <span data-ttu-id="aaf2a-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="aaf2a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaf2a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aaf2a-111">Requirements</span></span>  
 <span data-ttu-id="aaf2a-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aaf2a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf2a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aaf2a-113">See Also</span></span>  
 [<span data-ttu-id="aaf2a-114">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="aaf2a-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
