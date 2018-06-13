---
title: ISymUnmanagedWriter::SetUserEntryPoint — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ec44d4c2757555c74fe7fc27c26cc5fc87c4517
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426690"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="fec12-102">ISymUnmanagedWriter::SetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="fec12-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="fec12-103">Określa metodę zdefiniowane przez użytkownika, który jest punkt wejścia dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="fec12-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="fec12-104">Ten punkt wejścia można na przykład metoda głównego użytkownika zamiast generowane przez kompilator klas zastępczych przed funkcją main.</span><span class="sxs-lookup"><span data-stu-id="fec12-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fec12-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fec12-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fec12-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fec12-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="fec12-107">[in] Token metadanych metodę, która jest wpisu użytkownika punktu.</span><span class="sxs-lookup"><span data-stu-id="fec12-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fec12-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fec12-108">Return Value</span></span>  
 <span data-ttu-id="fec12-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fec12-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fec12-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fec12-110">Requirements</span></span>  
 <span data-ttu-id="fec12-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fec12-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec12-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fec12-112">See Also</span></span>  
 [<span data-ttu-id="fec12-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="fec12-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
