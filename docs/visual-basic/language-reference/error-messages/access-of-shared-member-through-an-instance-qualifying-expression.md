---
title: Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751608"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="f9a37-102">Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane</span><span class="sxs-lookup"><span data-stu-id="f9a37-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="f9a37-103">Zmienna wystąpienia klasy lub struktury jest używana, aby uzyskać dostęp do `Shared` zmiennej, właściwość, procedura lub zdarzenia, zdefiniowany w tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f9a37-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="f9a37-104">To ostrzeżenie może również wystąpić, jeśli zmienną instance umożliwia dostęp do niejawnie udostępnionego elementu członkowskiego klasy lub struktury, takiej jak stała wyliczenia, lub zagnieżdżona klasa lub Struktura.</span><span class="sxs-lookup"><span data-stu-id="f9a37-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="f9a37-105">Udostępnianie członka ma na celu tworzenie tylko jednej kopii tego elementu członkowskiego i udostępnić pojedynczej kopii każdego wystąpienia klasy lub struktury, w którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="f9a37-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="f9a37-106">Jest ona zgodna z dostępu do tego celu `Shared` elementu członkowskiego za pośrednictwem nazwy klasy lub struktury, a nie za pomocą zmienna, która zawiera poszczególne wystąpienia tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f9a37-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="f9a37-107">Uzyskiwanie dostępu do `Shared` elementu członkowskiego przez zmienną instance, może uczynić kod trudniejszy do zrozumienia przez fakt, że składowa jest przesłaniania `Shared`.</span><span class="sxs-lookup"><span data-stu-id="f9a37-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="f9a37-108">Ponadto, jeśli taki dostęp jest częścią wyrażenia wykonująca innych działań, takich jak `Function` procedury, która zwraca wystąpienie do udostępnionej składowej, Visual Basic pomija wyrażenie i innych akcji, w przeciwnym razie wykona.</span><span class="sxs-lookup"><span data-stu-id="f9a37-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="f9a37-109">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="f9a37-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="f9a37-110">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="f9a37-110">By default, this message is a warning.</span></span> <span data-ttu-id="f9a37-111">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f9a37-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f9a37-112">**Identyfikator błędu:** BC42025</span><span class="sxs-lookup"><span data-stu-id="f9a37-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9a37-113">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f9a37-113">To correct this error</span></span>  
  
- <span data-ttu-id="f9a37-114">Użyj nazwy klasy lub struktury, która definiuje `Shared` członka do niego dostęp, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9a37-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="f9a37-115">Być alert dotyczący skutków zakresu, jeśli dwa elementy programowania mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="f9a37-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="f9a37-116">W poprzednim przykładzie, jeśli zadeklarować wystąpienia przy użyciu `Dim testClass as testClass = Nothing`, kompilator traktuje wywołanie `testClass.sayHello()` po wystąpieniu dostępu metody przy użyciu nazwy klasy i bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f9a37-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a37-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9a37-117">See also</span></span>

- [<span data-ttu-id="f9a37-118">Shared</span><span class="sxs-lookup"><span data-stu-id="f9a37-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="f9a37-119">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9a37-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
