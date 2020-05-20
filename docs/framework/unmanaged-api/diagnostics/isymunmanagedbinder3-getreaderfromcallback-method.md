---
title: ISymUnmanagedBinder3::GetReaderFromCallback — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: 4a23e9aa259f430c0d0579657952fc6aba4c307c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441659"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="4f264-102">ISymUnmanagedBinder3::GetReaderFromCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f264-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="4f264-103">Zezwala użytkownikowi na implementowanie lub dostarczanie za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` uzyskanie informacji o katalogu debugowania z pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f264-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f264-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f264-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f264-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f264-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="4f264-106">podczas Wskaźnik do interfejsu importowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="4f264-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="4f264-107">podczas Wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4f264-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="4f264-108">podczas Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="4f264-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="4f264-109">podczas Wartość wyliczenia [CorSymSearchPolicyAttributes —](corsymsearchpolicyattributes-enumeration.md) , która określa zasady, które mają być używane podczas wyszukiwania czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="4f264-109">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="4f264-110">podczas Wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4f264-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4f264-111">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4f264-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f264-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4f264-112">Return Value</span></span>  
 <span data-ttu-id="4f264-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4f264-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f264-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f264-114">Requirements</span></span>  
 <span data-ttu-id="4f264-115">**Nagłówek:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="4f264-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f264-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f264-116">See also</span></span>

- [<span data-ttu-id="4f264-117">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4f264-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
