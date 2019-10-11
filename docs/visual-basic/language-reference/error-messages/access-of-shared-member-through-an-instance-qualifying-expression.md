---
title: Dostęp do udostępnionej składowej przez wystąpienie; wyrażenie kwalifikujące nie zostanie obliczone
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 773a97c301e7cb5bec0234ae466d487ec9716437
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250351"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="b72e1-102">Dostęp do udostępnionej składowej przez wystąpienie; wyrażenie kwalifikujące nie zostanie obliczone</span><span class="sxs-lookup"><span data-stu-id="b72e1-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>

<span data-ttu-id="b72e1-103">Zmienna wystąpienia klasy lub struktury jest używana w celu uzyskania dostępu do zmiennej `Shared`, właściwości, procedury lub zdarzenia zdefiniowanego w tej klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="b72e1-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="b72e1-104">To ostrzeżenie może również wystąpić, jeśli zmienna wystąpienia jest używana w celu uzyskania dostępu do niejawnie udostępnionej składowej klasy lub struktury, takiej jak stała lub Wyliczenie lub zagnieżdżona Klasa lub struktura.</span><span class="sxs-lookup"><span data-stu-id="b72e1-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>

<span data-ttu-id="b72e1-105">Celem udostępniania elementu członkowskiego jest utworzenie tylko jednej kopii tego elementu członkowskiego i udostępnienie tej pojedynczej kopii każdemu wystąpieniu klasy lub struktury, w której jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="b72e1-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="b72e1-106">Jest to zgodne z tym celem, aby uzyskać dostęp do elementu członkowskiego `Shared` przy użyciu nazwy klasy lub struktury, a nie za pomocą zmiennej, która przechowuje pojedyncze wystąpienie tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b72e1-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>

<span data-ttu-id="b72e1-107">Dostęp do elementu członkowskiego `Shared` za pomocą zmiennej wystąpienia może utrudnić zrozumienie kodu przez zaciemnienie faktu, że element członkowski jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="b72e1-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="b72e1-108">Ponadto, jeśli taki dostęp jest częścią wyrażenia, które wykonuje inne czynności, takie jak procedura `Function` zwracająca wystąpienie udostępnionego elementu członkowskiego, Visual Basic pomija wyrażenie i wszelkie inne akcje, które w przeciwnym razie byłyby wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b72e1-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
<span data-ttu-id="b72e1-109">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b72e1-109">For more information and an example, see [Shared](../modifiers/shared.md).</span></span>  
  
<span data-ttu-id="b72e1-110">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="b72e1-110">By default, this message is a warning.</span></span> <span data-ttu-id="b72e1-111">Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b72e1-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
<span data-ttu-id="b72e1-112">**Identyfikator błędu:** BC42025</span><span class="sxs-lookup"><span data-stu-id="b72e1-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b72e1-113">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b72e1-113">To correct this error</span></span>  
  
<span data-ttu-id="b72e1-114">Użyj nazwy klasy lub struktury, która definiuje element członkowski `Shared`, aby uzyskać do niego dostęp, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b72e1-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example:</span></span>
  
```vb
Public Class TestClass
    Public Shared Sub SayHello()
        MsgBox("Hello")
    End Sub
End Class
  
Module Program
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New TestClass()
        tc.SayHello()
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        TestClass.SayHello()
    End Sub  
End Module  
```  
  
> [!NOTE]
> <span data-ttu-id="b72e1-115">Alert dotyczący efektów zakresu, gdy dwa elementy programistyczne mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="b72e1-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="b72e1-116">W poprzednim przykładzie, Jeśli zadeklarujesz wystąpienie przy użyciu `Dim testClass as testClass = Nothing`, kompilator traktuje wywołanie do `testClass.sayHello()` jako dostęp do metody za pomocą nazwy klasy i nie występuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b72e1-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b72e1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b72e1-117">See also</span></span>

- [<span data-ttu-id="b72e1-118">Udostępniać</span><span class="sxs-lookup"><span data-stu-id="b72e1-118">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="b72e1-119">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b72e1-119">Scope in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/scope.md)
