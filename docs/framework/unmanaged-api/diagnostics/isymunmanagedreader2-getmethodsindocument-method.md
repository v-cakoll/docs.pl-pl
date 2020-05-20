---
title: ISymUnmanagedReader2::GetMethodsInDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
ms.openlocfilehash: 68a0f9ec8793d465a6fa3b1cb6936eddd7be4c8f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615413"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="a4e03-102">ISymUnmanagedReader2::GetMethodsInDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4e03-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="a4e03-103">Pobiera każdą metodę, która zawiera informacje o wierszu w podanym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a4e03-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4e03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4e03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4e03-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a4e03-106">podczas Wskaźnik do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a4e03-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="a4e03-107">podczas `ULONG32`Wskazuje rozmiar `pRetVal` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4e03-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="a4e03-108">określoną Wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu, który musi zawierać metody.</span><span class="sxs-lookup"><span data-stu-id="a4e03-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a4e03-109">określoną Wskaźnik do buforu, który odbiera metody.</span><span class="sxs-lookup"><span data-stu-id="a4e03-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4e03-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a4e03-110">Return Value</span></span>  
 <span data-ttu-id="a4e03-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a4e03-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e03-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4e03-112">Requirements</span></span>  
 <span data-ttu-id="a4e03-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a4e03-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e03-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4e03-114">See also</span></span>

- [<span data-ttu-id="a4e03-115">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a4e03-115">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
