---
title: ISymUnmanagedReader::UpdateSymbolStore — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfc4507557102e19d95f1b746b3a76a231882d7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736743"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="81db0-102">ISymUnmanagedReader::UpdateSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="81db0-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="81db0-103">Aktualizuje istniejący magazyn symboli w magazynie symboli delta.</span><span class="sxs-lookup"><span data-stu-id="81db0-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="81db0-104">Ta metoda jest używana w scenariuszach edit-and-continue można zaktualizować magazynu symboli, aby dopasować różnic do oryginalnego przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="81db0-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81db0-105">Należy określić tylko jeden z `filename` lub `pIStream` parametrów, nie obydwa.</span><span class="sxs-lookup"><span data-stu-id="81db0-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="81db0-106">Jeśli `filename` określono magazynu symboli, które zostaną zaktualizowane przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="81db0-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="81db0-107">Jeśli `pIStream` określono magazynu zostaną zaktualizowane przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="81db0-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81db0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="81db0-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81db0-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="81db0-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="81db0-110">[in] Nazwa pliku który zawiera magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="81db0-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="81db0-111">[in] Strumień pliku używana jako alternatywa `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="81db0-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81db0-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81db0-112">Return Value</span></span>  
 <span data-ttu-id="81db0-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="81db0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81db0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81db0-114">Requirements</span></span>  
 <span data-ttu-id="81db0-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="81db0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81db0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81db0-116">See also</span></span>

- [<span data-ttu-id="81db0-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="81db0-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
