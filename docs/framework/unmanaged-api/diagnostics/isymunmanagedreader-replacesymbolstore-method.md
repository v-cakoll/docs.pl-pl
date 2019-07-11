---
title: ISymUnmanagedReader::ReplaceSymbolStore — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 525ec4828fb942aeb447940ea68a523cd7c69140
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736725"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="ef571-102">ISymUnmanagedReader::ReplaceSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef571-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="ef571-103">Zamienia istniejący magazyn symboli w magazynie symboli delta.</span><span class="sxs-lookup"><span data-stu-id="ef571-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="ef571-104">Ta metoda jest podobna do [updatesymbolstore —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody, chyba że dany delta działa jako całkowitego zastąpienia, a nie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="ef571-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef571-105">Należy określić tylko jeden z `filename` lub `pIStream` parametrów, nie obydwa.</span><span class="sxs-lookup"><span data-stu-id="ef571-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="ef571-106">Jeśli `filename` określono magazynu symboli, które zostaną zaktualizowane przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="ef571-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="ef571-107">Jeśli `pIStream` określono magazynu zostaną zaktualizowane przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="ef571-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef571-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef571-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef571-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef571-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="ef571-110">[in] Nazwa pliku zawierającego magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="ef571-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ef571-111">[in] Strumień pliku używana jako alternatywa `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="ef571-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef571-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef571-112">Return Value</span></span>  
 <span data-ttu-id="ef571-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ef571-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef571-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef571-114">Requirements</span></span>  
 <span data-ttu-id="ef571-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef571-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef571-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef571-116">See also</span></span>

- [<span data-ttu-id="ef571-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef571-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
