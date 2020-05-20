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
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441880"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="27849-102">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="27849-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="27849-103">Zawiera informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="27849-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27849-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27849-104">Methods</span></span>  
  
|<span data-ttu-id="27849-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27849-105">Method</span></span>|<span data-ttu-id="27849-106">Opis</span><span class="sxs-lookup"><span data-stu-id="27849-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27849-107">GetDocumentsForMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="27849-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="27849-108">Pobiera dokumenty, w których ta metoda zawiera wiersze.</span><span class="sxs-lookup"><span data-stu-id="27849-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="27849-109">GetDocumentsForMethodCount, metoda</span><span class="sxs-lookup"><span data-stu-id="27849-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="27849-110">Pobiera liczbę dokumentów, w których ta metoda zawiera wiersze.</span><span class="sxs-lookup"><span data-stu-id="27849-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="27849-111">GetFileNameFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="27849-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="27849-112">Pobiera nazwę pliku dla wiersza skojarzonego z przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="27849-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="27849-113">GetLineFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="27849-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="27849-114">Pobiera informacje o wierszu skojarzone z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="27849-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="27849-115">GetSourceExtentInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="27849-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="27849-116">Pobiera najmniejszą linię początkową i największą linię końcową dla metody w określonym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="27849-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27849-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27849-117">Requirements</span></span>  
 <span data-ttu-id="27849-118">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="27849-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27849-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27849-119">See also</span></span>

- [<span data-ttu-id="27849-120">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="27849-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
