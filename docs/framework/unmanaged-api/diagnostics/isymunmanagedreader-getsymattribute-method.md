---
title: ISymUnmanagedReader::GetSymAttribute — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 763e698c7149de0fee61770e601032a4160b839f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378577"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="8445a-102">ISymUnmanagedReader::GetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="8445a-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="8445a-103">Pobiera atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="8445a-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="8445a-104">W przeciwieństwie do metadanych atrybutów niestandardowych te atrybuty niestandardowe są przechowywane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="8445a-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8445a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8445a-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8445a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8445a-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="8445a-107">[in] Token metadanych dla obiektu, dla którego żądana jest atrybut.</span><span class="sxs-lookup"><span data-stu-id="8445a-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="8445a-108">[in] Wskaźnik do zmiennej, która wskazuje atrybut do pobrania.</span><span class="sxs-lookup"><span data-stu-id="8445a-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="8445a-109">[in] Rozmiar `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8445a-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="8445a-110">[out] Wskaźnik do zmiennej, która odbiera długość danych atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8445a-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8445a-111">[out] Wskaźnik do zmiennej, która odbiera dane atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8445a-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8445a-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8445a-112">Return Value</span></span>  
 <span data-ttu-id="8445a-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="8445a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8445a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8445a-114">Requirements</span></span>  
 <span data-ttu-id="8445a-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8445a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8445a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8445a-116">See also</span></span>
- [<span data-ttu-id="8445a-117">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="8445a-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
