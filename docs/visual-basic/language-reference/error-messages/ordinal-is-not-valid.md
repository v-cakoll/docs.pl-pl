---
title: "Liczba porządkowa nie jest prawidłowa"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="b61b5-102">Liczba porządkowa nie jest prawidłowa</span><span class="sxs-lookup"><span data-stu-id="b61b5-102">Ordinal is not valid</span></span>
<span data-ttu-id="b61b5-103">Wskazane jest używany numer zamiast nazwę procedury wywołania do biblioteki dołączanej (dynamicznie DLL) przy użyciu `#num` składni.</span><span class="sxs-lookup"><span data-stu-id="b61b5-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="b61b5-104">Ten błąd ma następujące możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="b61b5-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="b61b5-105">Próba konwersji `#num` wyrażenie numeru porządkowego nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b61b5-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="b61b5-106">`#num` Określony nie określa żadnych funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="b61b5-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="b61b5-107">Biblioteki typów ma nieprawidłową deklaracją, co powoduje wewnętrzne korzystanie z nieprawidłową liczbą porządkową.</span><span class="sxs-lookup"><span data-stu-id="b61b5-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b61b5-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b61b5-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="b61b5-109">Upewnij się, że wyrażenie reprezentuje prawidłową liczbę lub wywołania tej procedury według nazwy.</span><span class="sxs-lookup"><span data-stu-id="b61b5-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="b61b5-110">Upewnij się, że `#num` identyfikuje prawidłowe funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="b61b5-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="b61b5-111">Izolowanie wywoływania przyczyną problemu przez komentarzy kodu.</span><span class="sxs-lookup"><span data-stu-id="b61b5-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="b61b5-112">Zapis `Declare` instrukcji dla procedury i raportu problem z dostawcą biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b61b5-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61b5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b61b5-113">See Also</span></span>  
 [<span data-ttu-id="b61b5-114">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="b61b5-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
