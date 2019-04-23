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
ms.openlocfilehash: f62c954bf9d73ab564eba388e742794a330362d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080504"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="64e61-102">ISymUnmanagedReader::UpdateSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="64e61-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="64e61-103">Aktualizuje istniejący magazyn symboli w magazynie symboli delta.</span><span class="sxs-lookup"><span data-stu-id="64e61-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="64e61-104">Ta metoda jest używana w scenariuszach edit-and-continue można zaktualizować magazynu symboli, aby dopasować różnic do oryginalnego przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="64e61-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64e61-105">Należy określić tylko jeden z `filename` lub `pIStream` parametrów, nie obydwa.</span><span class="sxs-lookup"><span data-stu-id="64e61-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="64e61-106">Jeśli `filename` określono magazynu symboli, które zostaną zaktualizowane przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="64e61-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="64e61-107">Jeśli `pIStream` określono magazynu zostaną zaktualizowane przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="64e61-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e61-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="64e61-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64e61-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="64e61-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="64e61-110">[in] Nazwa pliku który zawiera magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="64e61-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="64e61-111">[in] Strumień pliku używana jako alternatywa `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="64e61-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64e61-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="64e61-112">Return Value</span></span>  
 <span data-ttu-id="64e61-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="64e61-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e61-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64e61-114">Requirements</span></span>  
 <span data-ttu-id="64e61-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="64e61-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e61-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64e61-116">See also</span></span>

- [<span data-ttu-id="64e61-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="64e61-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
