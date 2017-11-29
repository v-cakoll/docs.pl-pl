---
title: "ISymUnmanagedDocument::GetCheckSum — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b0b2ce6facf99b44f54e8880d4436ab7fe96e50a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="a2dc3-102">ISymUnmanagedDocument::GetCheckSum — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2dc3-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="a2dc3-103">Pobiera sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2dc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2dc3-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2dc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2dc3-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="a2dc3-106">[in] Długość buforu podał `data` parametru</span><span class="sxs-lookup"><span data-stu-id="a2dc3-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="a2dc3-107">[out] Rozmiar i długość sumy kontrolnej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="a2dc3-108">[out] Buforu, który odbiera sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2dc3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2dc3-109">Return Value</span></span>  
 <span data-ttu-id="a2dc3-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a2dc3-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2dc3-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2dc3-111">See Also</span></span>  
 [<span data-ttu-id="a2dc3-112">ISymUnmanagedDocument — interfejs</span><span class="sxs-lookup"><span data-stu-id="a2dc3-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
