---
title: Liczba porządkowa nie jest prawidłowa
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 740243c744a7ba5391659894812a00d80555fd80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665665"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="972d2-102">Liczba porządkowa nie jest prawidłowa</span><span class="sxs-lookup"><span data-stu-id="972d2-102">Ordinal is not valid</span></span>
<span data-ttu-id="972d2-103">Wywołania do biblioteki dołączanej (dynamicznie DLL) wskazane Użyj numeru zamiast nazwy procedury przy użyciu `#num` składni.</span><span class="sxs-lookup"><span data-stu-id="972d2-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="972d2-104">Ten błąd ma następujące możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="972d2-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="972d2-105">Próba konwersji `#num` wyrażenie numeru porządkowego nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="972d2-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="972d2-106">`#num` Określonego nie określa żadnej funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="972d2-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="972d2-107">Biblioteka typów ma nieprawidłową deklarację skutkuje wewnętrzne korzystanie z nieprawidłową liczbą porządkową.</span><span class="sxs-lookup"><span data-stu-id="972d2-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="972d2-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="972d2-108">To correct this error</span></span>  
  
1. <span data-ttu-id="972d2-109">Upewnij się, że wyrażenie reprezentuje prawidłową liczbę, lub wywołaj procedurę według nazwy.</span><span class="sxs-lookup"><span data-stu-id="972d2-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="972d2-110">Upewnij się, że `#num` określa prawidłowe funkcję w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="972d2-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="972d2-111">Izolowanie po wywołaniu procedury, które powoduje problem, zakomentowując kodu.</span><span class="sxs-lookup"><span data-stu-id="972d2-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="972d2-112">Zapis `Declare` poufności informacji dotyczące procedury i raport problem z dostawcą biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="972d2-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972d2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="972d2-113">See also</span></span>

- [<span data-ttu-id="972d2-114">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="972d2-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
