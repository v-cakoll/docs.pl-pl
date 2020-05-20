---
title: ISymUnmanagedWriter::UsingNamespace — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: e4348cc59924b65b6c6bb53a9c2a98f1a1161b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614737"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="9b4ff-102">ISymUnmanagedWriter::UsingNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b4ff-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="9b4ff-103">Określa, że dana w pełni kwalifikowana nazwa przestrzeni nazw jest używana w aktualnie otwartym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="9b4ff-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="9b4ff-104">Przestrzeń nazw będzie używana we wszystkich zakresach, które dziedziczą z aktualnie otwartego zakresu.</span><span class="sxs-lookup"><span data-stu-id="9b4ff-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="9b4ff-105">Zamknięcie bieżącego zakresu spowoduje również zatrzymanie korzystania z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9b4ff-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b4ff-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b4ff-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b4ff-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b4ff-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="9b4ff-108">podczas Wskaźnik do w pełni kwalifikowanej nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9b4ff-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b4ff-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9b4ff-109">Return Value</span></span>  
 <span data-ttu-id="9b4ff-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9b4ff-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b4ff-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b4ff-111">Requirements</span></span>  
 <span data-ttu-id="9b4ff-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9b4ff-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4ff-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b4ff-113">See also</span></span>

- [<span data-ttu-id="9b4ff-114">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9b4ff-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
