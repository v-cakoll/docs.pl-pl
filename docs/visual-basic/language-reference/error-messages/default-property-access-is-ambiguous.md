---
title: Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego członka „<defaultpropertyname>" interfejsu „<interfacename1>" i dziedziczonego członka „<defaultpropertyname>" interfejsu „<interfacename2>"
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 99d5dc2e0f8389f8c9e90786c4d9d0fa037eb828
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651422"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="8ce04-102">Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego członków\<defaultpropertyname > "interfejsu"\<interfacename1 > "i"\<defaultpropertyname > "interfejsu"\< interfacename2 > "</span><span class="sxs-lookup"><span data-stu-id="8ce04-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>
<span data-ttu-id="8ce04-103">Interfejs dziedziczy dwa interfejsy, z których każdy deklaruje domyślna właściwość o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8ce04-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="8ce04-104">Kompilator nie można rozpoznać dostępu do tej właściwości domyślnej bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="8ce04-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="8ce04-105">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="8ce04-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="8ce04-106">Po określeniu `testObj(1)`, kompilator próbuje rozpoznać ona domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ce04-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="8ce04-107">Istnieją dwie właściwości domyślne możliwe z powodu dziedziczonych interfejsach, kompilator sygnały tego błędu.</span><span class="sxs-lookup"><span data-stu-id="8ce04-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="8ce04-108">**Identyfikator błędu:** BC30686</span><span class="sxs-lookup"><span data-stu-id="8ce04-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ce04-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8ce04-109">To correct this error</span></span>  
  
- <span data-ttu-id="8ce04-110">Należy unikać dziedziczy wszystkie elementy członkowskie o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8ce04-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="8ce04-111">W poprzednim przykładzie Jeśli `testObj` nie trzeba wykonać jedną z elementów członkowskich, na przykład, `Iface2`, Zadeklaruj go w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ce04-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="8ce04-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="8ce04-112">-or-</span></span>  
  
- <span data-ttu-id="8ce04-113">Implementuje dziedziczącej interfejsu w klasie.</span><span class="sxs-lookup"><span data-stu-id="8ce04-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="8ce04-114">Następnie można wdrożyć wszystkich właściwości dziedziczonych pod różnymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="8ce04-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="8ce04-115">Jednak tylko jeden z nich może być domyślną właściwość klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="8ce04-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="8ce04-116">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="8ce04-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ce04-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ce04-117">See also</span></span>

- [<span data-ttu-id="8ce04-118">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8ce04-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
