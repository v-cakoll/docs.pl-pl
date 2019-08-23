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
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939009"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="6a80a-102">ISymUnmanagedReader::UpdateSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a80a-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="6a80a-103">Aktualizuje istniejący magazyn symboli przy użyciu magazynu symboli różnicowych.</span><span class="sxs-lookup"><span data-stu-id="6a80a-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="6a80a-104">Ta metoda jest używana w scenariuszach Edytuj i Kontynuuj, aby zaktualizować magazyn symboli tak, aby pasował do różnic w oryginalnym przenośnym pliku wykonywalnym (PE).</span><span class="sxs-lookup"><span data-stu-id="6a80a-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a80a-105">Należy określić tylko jeden z `filename` parametrów lub `pIStream` , ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="6a80a-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="6a80a-106">Jeśli `filename` jest określony, magazyn symboli zostanie zaktualizowany przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="6a80a-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="6a80a-107">Jeśli `pIStream` jest określony, magazyn zostanie zaktualizowany o dane <xref:System.Runtime.InteropServices.ComTypes.IStream>z.</span><span class="sxs-lookup"><span data-stu-id="6a80a-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a80a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a80a-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a80a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a80a-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="6a80a-110">podczas Nazwa pliku, który zawiera magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="6a80a-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="6a80a-111">podczas Strumień pliku używany jako alternatywa dla `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a80a-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a80a-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6a80a-112">Return Value</span></span>  
 <span data-ttu-id="6a80a-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie, E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6a80a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a80a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a80a-114">Requirements</span></span>  
 <span data-ttu-id="6a80a-115">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a80a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a80a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a80a-116">See also</span></span>

- [<span data-ttu-id="6a80a-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a80a-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
