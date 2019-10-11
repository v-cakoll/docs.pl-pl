---
title: Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego elementu członkowskiego interfejsu "<defaultpropertyname>" interfejsu "<interfacename1>" i "<defaultpropertyname>" interfejsu "<interfacename2>"
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: f76163d58f3f11d3ca946525a1604abc3ebba68d
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250366"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="05e5f-102">Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego elementu członkowskiego interfejsu "\<defaultpropertyname >" interfejsu "\<interfacename1 >" i "\<defaultpropertyname >" interfejsu "\<interfacename2 >"</span><span class="sxs-lookup"><span data-stu-id="05e5f-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="05e5f-103">Interfejs dziedziczy z dwóch interfejsów, z których każdy deklaruje właściwość domyślną o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="05e5f-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="05e5f-104">Kompilator nie może rozpoznać dostępu do tej właściwości domyślnej bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="05e5f-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="05e5f-105">Ilustruje to Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="05e5f-105">The following example illustrates this.</span></span>

```vb
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

<span data-ttu-id="05e5f-106">Po określeniu `testObj(1)` kompilator próbuje rozwiązać ten problem do właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="05e5f-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="05e5f-107">Istnieją jednak dwie możliwe właściwości domyślne ze względu na dziedziczone interfejsy, więc kompilator sygnalizuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="05e5f-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="05e5f-108">**Identyfikator błędu:** BC30686</span><span class="sxs-lookup"><span data-stu-id="05e5f-108">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="05e5f-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="05e5f-109">To correct this error</span></span>

- <span data-ttu-id="05e5f-110">Należy unikać dziedziczenia wszystkich elementów członkowskich o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="05e5f-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="05e5f-111">W poprzednim przykładzie, jeśli `testObj` nie potrzebuje żadnego z elementów członkowskich, powiedz `Iface2`, a następnie zadeklaruj go w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="05e5f-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="05e5f-112">\-or-</span><span class="sxs-lookup"><span data-stu-id="05e5f-112">\-or-</span></span>

- <span data-ttu-id="05e5f-113">Zaimplementuj interfejs dziedziczenia w klasie.</span><span class="sxs-lookup"><span data-stu-id="05e5f-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="05e5f-114">Następnie można zaimplementować każdą z dziedziczonych właściwości o różnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="05e5f-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="05e5f-115">Jednak tylko jeden z nich może być właściwością domyślną klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="05e5f-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="05e5f-116">Ilustruje to Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="05e5f-116">The following example illustrates this.</span></span>

  ```vb
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

## <a name="see-also"></a><span data-ttu-id="05e5f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05e5f-117">See also</span></span>

- [<span data-ttu-id="05e5f-118">Interfejsów</span><span class="sxs-lookup"><span data-stu-id="05e5f-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
