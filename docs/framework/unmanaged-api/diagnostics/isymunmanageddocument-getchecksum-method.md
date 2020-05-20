---
title: ISymUnmanagedDocument::GetCheckSum — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 543bd208e5492460435663c32f276472a763f613
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441100"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="81cb3-102">ISymUnmanagedDocument::GetCheckSum — Metoda</span><span class="sxs-lookup"><span data-stu-id="81cb3-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="81cb3-103">Pobiera sumę kontrolną.</span><span class="sxs-lookup"><span data-stu-id="81cb3-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81cb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81cb3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81cb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81cb3-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="81cb3-106">podczas Długość buforu dostarczonego przez `data` parametr</span><span class="sxs-lookup"><span data-stu-id="81cb3-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="81cb3-107">określoną Rozmiar i długość sumy kontrolnej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="81cb3-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="81cb3-108">określoną Bufor, który odbiera sumę kontrolną.</span><span class="sxs-lookup"><span data-stu-id="81cb3-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81cb3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81cb3-109">Return Value</span></span>  
 <span data-ttu-id="81cb3-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="81cb3-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81cb3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81cb3-111">See also</span></span>

- [<span data-ttu-id="81cb3-112">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="81cb3-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
