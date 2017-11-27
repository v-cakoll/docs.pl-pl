---
title: "ISymUnmanagedReader::UpdateSymbolStore — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.UpdateSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cfea77814069f6689f7492608548836fdafa591b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="89788-102">ISymUnmanagedReader::UpdateSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="89788-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="89788-103">Aktualizuje istniejący magazyn symbol magazynu symboli delta.</span><span class="sxs-lookup"><span data-stu-id="89788-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="89788-104">Ta metoda jest używana w scenariuszach edit-and-continue można zaktualizować magazynu symboli do dopasowania delty do oryginalnego przenośnego (PE) pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="89788-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89788-105">Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba.</span><span class="sxs-lookup"><span data-stu-id="89788-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="89788-106">Jeśli `filename` określono magazyn symbol zostanie zaktualizowany przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="89788-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="89788-107">Jeśli `pIStream` określono magazyn zostanie zaktualizowany przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="89788-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89788-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="89788-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89788-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="89788-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="89788-110">[in] Nazwa pliku, który zawiera magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="89788-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="89788-111">[in] Strumień pliku używany zamiast `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="89788-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89788-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="89788-112">Return Value</span></span>  
 <span data-ttu-id="89788-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="89788-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89788-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89788-114">Requirements</span></span>  
 <span data-ttu-id="89788-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="89788-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89788-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89788-116">See Also</span></span>  
 [<span data-ttu-id="89788-117">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="89788-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
