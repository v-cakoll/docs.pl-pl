---
title: Właściwość „<propertyname>” nie zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 1788d06aa5236d4cfc33999df86ad72c420b41df
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269006"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="cd9a1-102">Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="cd9a1-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="cd9a1-103">Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="cd9a1-104">Może wystąpić wyjątek pustej referencji, w czasie wykonywania, gdy zostanie użyty wynik.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="cd9a1-105">Właściwość `Get` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kodu, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="cd9a1-106">Może zwracać wartość z właściwością `Get` procedury w dowolnym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="cd9a1-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="cd9a1-107">Przypisz wartości do danej nazwy właściwości, a następnie wykonaj `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="cd9a1-108">Przypisz wartości do danej nazwy właściwości, a następnie wykonaj `End Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="cd9a1-109">Zawiera wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd9a1-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="cd9a1-110">Jeśli kontrola przechodzi do `Exit Property` lub `End Get` i nie przypisano żadnej wartości Nazwa właściwości `Get` procedura zwraca wartość domyślną typu danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="cd9a1-111">Aby uzyskać więcej informacji, zobacz "Zachowanie" w [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd9a1-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="cd9a1-112">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-112">By default, this message is a warning.</span></span> <span data-ttu-id="cd9a1-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cd9a1-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cd9a1-114">**Identyfikator błędu:** BC42107</span><span class="sxs-lookup"><span data-stu-id="cd9a1-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd9a1-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cd9a1-115">To correct this error</span></span>  
  
-   <span data-ttu-id="cd9a1-116">Sprawdź logikę przepływu sterowania i upewnij się, że przypisanie wartości przed każdej instrukcji, który powoduje, że wynik.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="cd9a1-117">Ułatwia to zagwarantować, każdy zwracany z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="cd9a1-118">Jeśli to zrobisz, ostatnią instrukcję przed `End Get` powinien być `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cd9a1-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd9a1-119">See also</span></span>
- [<span data-ttu-id="cd9a1-120">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="cd9a1-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="cd9a1-121">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="cd9a1-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="cd9a1-122">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd9a1-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
