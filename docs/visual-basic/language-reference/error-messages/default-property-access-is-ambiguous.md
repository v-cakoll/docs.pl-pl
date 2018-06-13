---
title: Dostęp do właściwości domyślnej jest niejednoznaczny między elementami członkowskimi odziedziczonego interfejsu &#39; &lt;defaultpropertyname&gt; &#39; interfejsu &#39; &lt;interfacename1&gt; &#39; i &#39; &lt;defaultpropertyname&gt; &#39; interfejsu &#39; &lt;interfacename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 65a10067284cad3bf56ecdc441ebefa0a740ef53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590858"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="5fe14-102">Dostęp do właściwości domyślnej jest niejednoznaczny między elementami członkowskimi odziedziczonego interfejsu &#39; &lt;defaultpropertyname&gt; &#39; interfejsu &#39; &lt;interfacename1&gt; &#39; i &#39; &lt;defaultpropertyname&gt; &#39; interfejsu &#39; &lt;interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="5fe14-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="5fe14-103">Interfejs dziedziczy dwa interfejsy, z których każdy deklaruje domyślna właściwość o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5fe14-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="5fe14-104">Kompilator nie można rozpoznać dostęp do tej właściwości domyślnej bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="5fe14-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="5fe14-105">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="5fe14-105">The following example illustrates this.</span></span>  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5fe14-106">Po określeniu `testObj(1)`, kompilator próbuje rozpoznać ona domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5fe14-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="5fe14-107">Istnieją dwa możliwe domyślnych właściwości z powodu dziedziczonych interfejsach, dlatego kompilator sygnały tego błędu.</span><span class="sxs-lookup"><span data-stu-id="5fe14-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="5fe14-108">**Identyfikator błędu:** BC30686</span><span class="sxs-lookup"><span data-stu-id="5fe14-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5fe14-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5fe14-109">To correct this error</span></span>  
  
-   <span data-ttu-id="5fe14-110">Unikaj dziedziczenie żadnych elementów członkowskich o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5fe14-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="5fe14-111">W poprzednim przykładzie Jeśli `testObj` nie wymaga żadnego z elementów członkowskich, co oznacza, `Iface2`, Zadeklaruj ją w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5fe14-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="5fe14-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="5fe14-112">-or-</span></span>  
  
-   <span data-ttu-id="5fe14-113">Zaimplementuj interfejs dziedziczących w klasie.</span><span class="sxs-lookup"><span data-stu-id="5fe14-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="5fe14-114">Następnie można wdrożyć wszystkich właściwości dziedziczone o różnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="5fe14-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="5fe14-115">Jednak tylko jeden z nich może być domyślną właściwość klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="5fe14-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="5fe14-116">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="5fe14-116">The following example illustrates this.</span></span>  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5fe14-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fe14-117">See Also</span></span>  
 [<span data-ttu-id="5fe14-118">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5fe14-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
