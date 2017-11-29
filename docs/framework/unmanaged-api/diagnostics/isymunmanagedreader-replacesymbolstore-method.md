---
title: "ISymUnmanagedReader::ReplaceSymbolStore — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.ReplaceSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09bcad4898cf4d3310a96164bdc82006e185006f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="6ec24-102">ISymUnmanagedReader::ReplaceSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ec24-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="6ec24-103">Zamienia istniejący magazyn symbol magazynu symboli delta.</span><span class="sxs-lookup"><span data-stu-id="6ec24-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="6ec24-104">Ta metoda jest podobna do [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody, z wyjątkiem, że dany delta działa jako całkowite zastąpienie, a nie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="6ec24-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ec24-105">Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba.</span><span class="sxs-lookup"><span data-stu-id="6ec24-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="6ec24-106">Jeśli `filename` określono magazyn symbol zostanie zaktualizowany przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="6ec24-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="6ec24-107">Jeśli `pIStream` określono magazyn zostanie zaktualizowany przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="6ec24-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec24-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ec24-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ec24-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ec24-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="6ec24-110">[in] Nazwa pliku zawierającego magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="6ec24-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="6ec24-111">[in] Strumień pliku używany zamiast `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="6ec24-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ec24-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ec24-112">Return Value</span></span>  
 <span data-ttu-id="6ec24-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6ec24-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec24-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ec24-114">Requirements</span></span>  
 <span data-ttu-id="6ec24-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ec24-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec24-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ec24-116">See Also</span></span>  
 [<span data-ttu-id="6ec24-117">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="6ec24-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
