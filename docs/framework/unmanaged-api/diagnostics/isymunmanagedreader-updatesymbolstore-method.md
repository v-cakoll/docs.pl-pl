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
ms.openlocfilehash: e052d9b7b2abd57b176dfe3b00afac626d422c58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446458"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="316a5-102">ISymUnmanagedReader::UpdateSymbolStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="316a5-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="316a5-103">Aktualizuje istniejący magazyn symboli przy użyciu magazynu symboli różnicowych.</span><span class="sxs-lookup"><span data-stu-id="316a5-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="316a5-104">Ta metoda jest używana w scenariuszach Edytuj i Kontynuuj, aby zaktualizować magazyn symboli tak, aby pasował do różnic w oryginalnym przenośnym pliku wykonywalnym (PE).</span><span class="sxs-lookup"><span data-stu-id="316a5-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="316a5-105">Należy określić tylko jeden z parametrów `filename` lub `pIStream`, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="316a5-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="316a5-106">Jeśli `filename` jest określony, magazyn symboli zostanie zaktualizowany przy użyciu symboli w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="316a5-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="316a5-107">W przypadku określenia `pIStream` magazyn zostanie zaktualizowany o dane z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="316a5-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316a5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="316a5-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="316a5-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="316a5-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="316a5-110">podczas Nazwa pliku, który zawiera magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="316a5-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="316a5-111">podczas Strumień pliku używany jako alternatywa dla parametru `filename`.</span><span class="sxs-lookup"><span data-stu-id="316a5-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="316a5-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="316a5-112">Return Value</span></span>  
 <span data-ttu-id="316a5-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="316a5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="316a5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="316a5-114">Requirements</span></span>  
 <span data-ttu-id="316a5-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="316a5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316a5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="316a5-116">See also</span></span>

- [<span data-ttu-id="316a5-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="316a5-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
