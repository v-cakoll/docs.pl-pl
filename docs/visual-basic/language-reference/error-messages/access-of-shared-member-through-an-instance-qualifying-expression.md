---
title: Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="0a876-102">Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane</span><span class="sxs-lookup"><span data-stu-id="0a876-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="0a876-103">Zmienna wystąpienia klasy lub struktury jest używana do dostępu `Shared` zmienną, właściwością, procedura lub zdarzeń zdefiniowanych w tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0a876-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="0a876-104">To ostrzeżenie może również wystąpić, jeśli zmienna wystąpienia są używane do uzyskania dostępu niejawnie udostępnionego elementu członkowskiego klasy lub struktury, takich jak stałą lub wyliczenia, lub zagnieżdżone klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0a876-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="0a876-105">Udostępnianie element członkowski ma na celu tworzenie tylko jednej kopii tego członka i udostępnić tym pojedynczej kopii każdego wystąpienia klasy lub struktury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="0a876-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="0a876-106">Jest ona zgodna z dostępu do tego celu `Shared` elementu członkowskiego za pomocą nazwy klasy lub struktury, a nie za pośrednictwem zmiennej, która przechowuje poszczególne wystąpienia tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0a876-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="0a876-107">Uzyskiwanie dostępu do `Shared` użytkownika za pomocą zmienna wystąpienia może utrudnić kodu bardziej zrozumiałe przesłaniania fakt, że element członkowski jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="0a876-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="0a876-108">Ponadto, jeśli taki dostęp jest częścią wyrażenia wykonująca inne akcje, takie jak `Function` procedury, która zwraca wystąpienie klasy udostępnionego elementu członkowskiego [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pomija wyrażenie i inne akcje, w przeciwnym razie będzie wykonywać.</span><span class="sxs-lookup"><span data-stu-id="0a876-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="0a876-109">Aby uzyskać więcej informacji i przykład zobacz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0a876-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="0a876-110">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="0a876-110">By default, this message is a warning.</span></span> <span data-ttu-id="0a876-111">Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0a876-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0a876-112">**Identyfikator błędu:** BC42025</span><span class="sxs-lookup"><span data-stu-id="0a876-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a876-113">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0a876-113">To correct this error</span></span>  
  
-   <span data-ttu-id="0a876-114">Użyj nazwy klasy lub struktury, który definiuje `Shared` elementu członkowskiego dostępu do niego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a876-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="0a876-115">Być alert dotyczący skutków zakresu, jeśli dwa elementy programowania mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="0a876-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="0a876-116">W poprzednim przykładzie, jeśli Zadeklaruj wystąpienie za pomocą `Dim testClass as testClass = Nothing`, kompilator traktuje wywołanie `testClass.sayHello()` jako dostępu metody za pomocą nazwy klasy i ostrzeżenie nie występuje.</span><span class="sxs-lookup"><span data-stu-id="0a876-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a876-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a876-117">See Also</span></span>  
 [<span data-ttu-id="0a876-118">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="0a876-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="0a876-119">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a876-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
