---
title: ISymENCUnmanagedMethod — Interfejs
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4474269688094ea6c81b06659727acfb9c2ad6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940260"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="4d0a9-102">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4d0a9-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="4d0a9-103">Informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="4d0a9-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d0a9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d0a9-104">Methods</span></span>  
  
|<span data-ttu-id="4d0a9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d0a9-105">Method</span></span>|<span data-ttu-id="4d0a9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4d0a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d0a9-107">GetDocumentsForMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="4d0a9-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="4d0a9-108">Pobiera dokumentów, dla których ta metoda powoduje wierszy.</span><span class="sxs-lookup"><span data-stu-id="4d0a9-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="4d0a9-109">GetDocumentsForMethodCount, metoda</span><span class="sxs-lookup"><span data-stu-id="4d0a9-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="4d0a9-110">Pobiera liczbę dokumentów, które ta metoda powoduje wierszy.</span><span class="sxs-lookup"><span data-stu-id="4d0a9-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="4d0a9-111">GetFileNameFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="4d0a9-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="4d0a9-112">Pobiera nazwę pliku dla linii skojarzonych z przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="4d0a9-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="4d0a9-113">GetLineFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="4d0a9-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="4d0a9-114">Pobiera informacje o wiersz skojarzony z przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="4d0a9-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="4d0a9-115">GetSourceExtentInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="4d0a9-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="4d0a9-116">Pobiera najmniejszą liczbę linii i uruchomić największy wiersz końcowy w metodzie w określonym dokumentem.</span><span class="sxs-lookup"><span data-stu-id="4d0a9-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d0a9-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d0a9-117">Requirements</span></span>  
 <span data-ttu-id="4d0a9-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d0a9-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0a9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d0a9-119">See also</span></span>

- [<span data-ttu-id="4d0a9-120">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="4d0a9-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
