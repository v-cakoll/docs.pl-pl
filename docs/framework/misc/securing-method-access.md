---
title: "Zabezpieczanie dostępu metody"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36c8ae484120fc835bf341d37cda72b22b401117
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="securing-method-access"></a>Zabezpieczanie dostępu metody
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 W przypadku niektórych metod może nie nadawać się do dowolnego kodu niezaufanej do wywołania. Takie metody stanowić zagrożenie kilka: metoda może zawierać niektórych ograniczone informacje; może być podejrzeń wszelkie informacje przekazywane może nie sprawdzanie błędów dla parametrów; lub z niewłaściwego parametrami, może być nieprawidłowe działanie lub czymś szkodliwe. Należy należy pamiętać o tych przypadkach i podjąć działania w celu ochrony metody.  
  
 W niektórych przypadkach może być konieczne ograniczanie metod, które nie są przeznaczone do użytku publicznego, ale nadal muszą być publiczne. Na przykład może być interfejs, który musi być wywoływany przez własnych bibliotek DLL i dlatego muszą być publiczne, ale nie chcesz udostępnić go publicznie, aby uniemożliwić klientom korzystanie z niego lub aby uniemożliwić wykorzystanie punktem wejścia do składnika złośliwego kodu. Kolejny powód wspólnej do ograniczania metody nie przeznaczony do użytku publicznego (ale który muszą być publiczne) jest, aby uniknąć konieczności dokumentów i obsługi, co może być bardzo wewnętrznej.  
  
 Zarządzany kod oferuje kilka sposobów do ograniczania dostępu do metody:  
  
-   Ograniczenie zakresu ułatwień dostępu do klasy, zestawu lub klasy pochodne, jeśli może być zaufane. Jest to najprostszy sposób, aby ograniczyć dostęp do metody. Należy pamiętać, że klasy pochodne — ogólnie rzecz biorąc, może być mniej zaufanego niż klasa, które pochodzą one od, chociaż w niektórych przypadkach mają tożsamości klasy nadrzędnej. W szczególności nie wnioskować zaufanie od słowa kluczowego **chronione**, który nie jest zawsze używany w kontekście zabezpieczeń.  
  
-   Ograniczenia dostępu metody wywołań określoną tożsamością — zasadniczo żadnych określonego [dowód](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (silnej nazwy, wydawcy strefy i tak dalej) wybierz.  
  
-   Ograniczenia dostępu metody dotyczące obiektów wywołujących uzyskanie niezależnie od uprawnień, należy wybrać.  
  
 Podobnie zabezpieczenia deklaratywne pozwala na kontrolowanie dziedziczenia klas. Można użyć **InheritanceDemand** wykonać następujące czynności:  
  
-   Wymagaj klas pochodnych określona tożsamość lub uprawnienia.  
  
-   Wymagaj klas pochodnych przesłaniające konkretnych metod określona tożsamość lub uprawnienia.  
  
 Poniższy przykład pokazuje, jak w celu ochrony klasą publiczną ograniczony dostęp przez wymaganie, aby obiekty wywołujące były podpisane przy użyciu określonego silnej nazwy. W tym przykładzie użyto <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> z **żądanie** silnej nazwy. Oparty na zadaniach informacji na temat podpisać zestaw o silnej nazwie, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}   
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a>Wyłączanie klas i członków z zasobów używanych przez niezaufany kod  
 Użyj deklaracji w tej sekcji, aby zapobiec używany przez kod częściowo zaufany określonej klasy i metody, jak również właściwości i zdarzenia. Stosując deklaracji klasy, stosują ochronę do jego metod, właściwości i zdarzeń; jednak należy pamiętać, że dostęp do pola nie ma wpływu na zabezpieczenia deklaratywne. Należy też zauważyć, że linkdemand pomoże zapewnić ochronę przed tylko bezpośredniego wywoływania i nadal mogą być narażone na ataki zapewnienia.  
  
> [!NOTE]
>  Wprowadzono nowy model przezroczystość w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modelu identyfikuje bezpieczny kod z <xref:System.Security.SecurityCriticalAttribute> atrybutu. Kod krytyczny dla zabezpieczeń wymaga zarówno wywołań i dziedziczenia, mogą być w pełni zaufany. Zestawy, które działają w ramach zasad zabezpieczeń dostępu kodu z wcześniejszych wersji .NET Framework mogą wywoływać zestawy poziomu 2. W takim przypadku atrybuty krytyczny dla zabezpieczeń będą traktowane jako linkdemand dla pełnego zaufania.  
  
 W zestawy o silnych nazwach [LinkDemand](../../../docs/framework/misc/link-demands.md) jest stosowany do wszystkich publicznie dostępnych metod, właściwości i zdarzenia tam, aby ograniczyć ich stosowania do wywoływania w pełni zaufany. Aby wyłączyć tę funkcję, należy zastosować <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu. W związku z tym jawnie oznaczenie klasy do wykluczenia niezaufanych obiektów wywołujących jest niezbędne tylko w przypadku zestawy nieoznaczone lub zestawów z tym atrybutem; Możesz użyć tych deklaracjach tam zaznaczania podzbiór typy, które nie są przeznaczone do wywoływania w niezaufanych.  
  
 Poniższe przykłady przedstawiają sposób uniemożliwiać korzystanie w kodzie niezaufanym klas i członków.  
  
 Dla klas publicznych nonsealed:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _   
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 Dla publicznego zapieczętowane klasy:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 Dla publicznych klasy abstrakcyjne:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe{}  
```  
  
 Dla publicznych funkcji wirtualnych:  
  
```vb  
Class Base1   
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1   
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 Dla publicznych funkcje abstrakcyjne:  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 Dla funkcji publicznego zastąpienie, gdzie klasy podstawowej nie wymaga pełnego zaufania:  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{     
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]      
    public override void CanOverrideOrCallMe()   
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 Dla funkcji zastąpienie publicznych gdzie klasa podstawowa wymaga pełnego zaufania:  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe   
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{     
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]      
    public override void CanOverrideOrCallMe()   
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 Interfejsów publicznych:  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe   
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a>Wirtualne wewnętrzne zastąpienia lub przeciążenia zastępowanego przyjaciela klasy  
  
> [!NOTE]
>  W tej sekcji ostrzega o problem z zabezpieczeniami przy deklarowaniu metody jednocześnie jako `virtual` i `internal` (`Overloads``Overridable``Friend` w języku Visual Basic). To ostrzeżenie nie dotyczy wersji systemu .NET Framework 1.0 i 1.1, nie ma zastosowania do nowszych wersji.  
  
 W wersji systemu .NET Framework 1.0 i 1.1 należy pamiętać o nuance ułatwień dostępu systemu typu po potwierdzeniu, że kod jest niedostępne dla innych zestawów. Metoda, która jest zadeklarowana jako **wirtualnego** i **wewnętrzny** (**Overloads możliwym do zastąpienia Friend** w języku Visual Basic) można zastąpić wpis vtable klasy nadrzędnej i mogą być używane tylko z w ramach tego samego zestawu, ponieważ jest on wewnętrzny. Jednak ułatwień dostępu dla zastępowanie jest określany przez **wirtualnego** — słowo kluczowe, a to może zostać zastąpiona z innego zestawu, pod warunkiem, że kod ma dostęp do samej klasy. Jeśli możliwość zastąpienia stanowi problem, użyj zabezpieczenia deklaratywne, aby go rozwiązać, lub usuń **wirtualnego** — słowo kluczowe, jeśli nie jest ścisłym wymogiem.  
  
 Należy pamiętać, że nawet jeśli kompilatora języka uniemożliwia zastąpienia z powodu błędu kompilacji, możliwe kod napisany za pomocą inne kompilatory do zastąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
