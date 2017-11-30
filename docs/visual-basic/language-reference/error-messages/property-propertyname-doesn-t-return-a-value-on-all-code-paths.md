---
title: "Właściwości &#39; &lt;propertyname&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords: BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="03edf-102">Właściwości &#39; &lt;propertyname&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="03edf-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="03edf-103">Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="03edf-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="03edf-104">W czasie wykonywania, gdy zostanie użyty wynik może wystąpić wyjątek odwołania zerowego.</span><span class="sxs-lookup"><span data-stu-id="03edf-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="03edf-105">Właściwość `Get` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="03edf-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="03edf-106">Może zwracać wartości z właściwości `Get` procedury w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="03edf-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="03edf-107">Przypisuje wartość do nazwy właściwości, a następnie wykonaj `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03edf-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="03edf-108">Przypisuje wartość do nazwy właściwości, a następnie wykonaj `End Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03edf-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="03edf-109">Włącz wartość w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03edf-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="03edf-110">Jeśli formant przekazuje do `Exit Property` lub `End Get` i nie przypisano żadnej wartości do nazwy właściwości `Get` procedury zwraca wartość domyślna właściwości typu danych.</span><span class="sxs-lookup"><span data-stu-id="03edf-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="03edf-111">Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03edf-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="03edf-112">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="03edf-112">By default, this message is a warning.</span></span> <span data-ttu-id="03edf-113">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="03edf-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="03edf-114">**Identyfikator błędu:** BC42107</span><span class="sxs-lookup"><span data-stu-id="03edf-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03edf-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="03edf-115">To correct this error</span></span>  
  
-   <span data-ttu-id="03edf-116">Sprawdź logika przepływu sterowania i upewnij się, że można przypisać wartości przed każdym instrukcji, która powoduje, że typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="03edf-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="03edf-117">Ułatwia zagwarantować co zwrotu z procedury zwraca wartość, jeśli używasz zawsze `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03edf-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="03edf-118">Jeśli to zrobisz, ostatniej instrukcji przed `End Get` powinien być `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03edf-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03edf-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03edf-119">See Also</span></span>  
 [<span data-ttu-id="03edf-120">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="03edf-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="03edf-121">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="03edf-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="03edf-122">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="03edf-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
