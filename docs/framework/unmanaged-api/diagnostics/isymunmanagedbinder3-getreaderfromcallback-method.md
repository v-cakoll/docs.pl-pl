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
ms.openlocfilehash: a0cccc0adfc666cc8e373bc1f89c8f6f97068fde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449310"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="3451f-102">ISymUnmanagedBinder3::GetReaderFromCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="3451f-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="3451f-103">Zezwala użytkownikowi na implementowanie lub dostarczanie za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback`, aby uzyskać informacje o katalogu debugowania z pamięci.</span><span class="sxs-lookup"><span data-stu-id="3451f-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3451f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3451f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3451f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3451f-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="3451f-106">podczas Wskaźnik do interfejsu importowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="3451f-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="3451f-107">podczas Wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="3451f-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="3451f-108">podczas Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="3451f-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="3451f-109">podczas Wartość wyliczenia [CorSymSearchPolicyAttributes —](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) , która określa zasady, które mają być używane podczas wyszukiwania czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="3451f-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="3451f-110">podczas Wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3451f-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3451f-111">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3451f-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3451f-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="3451f-112">Return Value</span></span>  
 <span data-ttu-id="3451f-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3451f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3451f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3451f-114">Requirements</span></span>  
 <span data-ttu-id="3451f-115">**Nagłówek:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="3451f-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3451f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3451f-116">See also</span></span>

- [<span data-ttu-id="3451f-117">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="3451f-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
