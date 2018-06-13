---
title: Właściwość &#39; &lt;propertyname&gt; &#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 72bc7e45cadd2528f29c88bf6e80ee5f381052dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594217"
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="1287e-102">Właściwość &#39; &lt;propertyname&gt; &#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="1287e-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="1287e-103">Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="1287e-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="1287e-104">W czasie wykonywania, gdy zostanie użyty wynik może wystąpić wyjątek odwołania zerowego.</span><span class="sxs-lookup"><span data-stu-id="1287e-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="1287e-105">Właściwość `Get` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="1287e-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="1287e-106">Może zwracać wartości z właściwości `Get` procedury w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="1287e-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="1287e-107">Przypisuje wartość do nazwy właściwości, a następnie wykonaj `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1287e-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="1287e-108">Przypisuje wartość do nazwy właściwości, a następnie wykonaj `End Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1287e-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="1287e-109">Włącz wartość w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1287e-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="1287e-110">Jeśli formant przekazuje do `Exit Property` lub `End Get` i nie przypisano żadnej wartości do nazwy właściwości `Get` procedury zwraca wartość domyślna właściwości typu danych.</span><span class="sxs-lookup"><span data-stu-id="1287e-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="1287e-111">Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1287e-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="1287e-112">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1287e-112">By default, this message is a warning.</span></span> <span data-ttu-id="1287e-113">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1287e-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1287e-114">**Identyfikator błędu:** BC42107</span><span class="sxs-lookup"><span data-stu-id="1287e-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1287e-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1287e-115">To correct this error</span></span>  
  
-   <span data-ttu-id="1287e-116">Sprawdź logika przepływu sterowania i upewnij się, że można przypisać wartości przed każdym instrukcji, która powoduje, że typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="1287e-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="1287e-117">Ułatwia zagwarantować co zwrotu z procedury zwraca wartość, jeśli używasz zawsze `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1287e-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="1287e-118">Jeśli to zrobisz, ostatniej instrukcji przed `End Get` powinien być `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1287e-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1287e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1287e-119">See Also</span></span>  
 [<span data-ttu-id="1287e-120">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="1287e-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="1287e-121">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1287e-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="1287e-122">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1287e-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
