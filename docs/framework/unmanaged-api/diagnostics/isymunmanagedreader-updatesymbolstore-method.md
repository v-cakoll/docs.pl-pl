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
ms.openlocfilehash: 81f9db872e9904d2297221e266be710837d0fb66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="c1eab-102">ISymUnmanagedReader::UpdateSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1eab-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="c1eab-103">Aktualizuje istniejący magazyn symbol magazynu symboli delta.</span><span class="sxs-lookup"><span data-stu-id="c1eab-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="c1eab-104">Ta metoda jest używana w scenariuszach edit-and-continue można zaktualizować magazynu symboli do dopasowania delty do oryginalnego przenośnego (PE) pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c1eab-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1eab-105">Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba.</span><span class="sxs-lookup"><span data-stu-id="c1eab-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="c1eab-106">Jeśli `filename` określono magazyn symbol zostanie zaktualizowany przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="c1eab-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="c1eab-107">Jeśli `pIStream` określono magazyn zostanie zaktualizowany przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="c1eab-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1eab-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1eab-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1eab-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1eab-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="c1eab-110">[in] Nazwa pliku, który zawiera magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="c1eab-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="c1eab-111">[in] Strumień pliku używany zamiast `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="c1eab-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1eab-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c1eab-112">Return Value</span></span>  
 <span data-ttu-id="c1eab-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c1eab-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1eab-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1eab-114">Requirements</span></span>  
 <span data-ttu-id="c1eab-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1eab-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1eab-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1eab-116">See Also</span></span>  
 [<span data-ttu-id="c1eab-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1eab-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
