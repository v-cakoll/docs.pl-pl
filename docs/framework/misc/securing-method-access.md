---
title: Zabezpieczanie dostępu metody
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9d423ef71b76b2dcbbf2812e13850922fb50ac0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625894"
---
# <a name="securing-method-access"></a>Zabezpieczanie dostępu metody
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Niektóre metody może nie być odpowiednie dla dowolnego niezaufanego kodu do wywołania. Takie metody stanowić zagrożenie kilka: Metoda może być podanie pewnych informacji w ograniczonym; może być uważa, wszelkie informacje przekazywane może nie sprawdzanie błędów dla parametrów; lub z niewłaściwego parametrami, może być nieprawidłowe działanie lub czymś szkodliwe. Należy należy pamiętać o tych przypadkach i podjąć działania w celu ochrony metody.  
  
 W niektórych przypadkach może być konieczne do ograniczania metody, które nie są przeznaczone do użytku publicznego, ale nadal muszą być publiczne. Na przykład może być interfejsem, który musi być wywoływany we własnych bibliotek DLL i dlatego musi być publiczna, ale nie chcesz udostępnić je publicznie, aby pozwolić użytkownikom korzystanie z niego lub uniemożliwić wykorzystanie punkt wejścia do składnika przez złośliwy kod. Kolejnym powodem wspólne do ograniczania metody nie jest przeznaczona do użytku publicznego (ale, muszą być publiczne) jest, aby uniknąć konieczności dokumentów i obsługi, co może być bardzo wewnętrznej.  
  
 Zarządzane kodu oferuje kilka sposobów, aby ograniczyć dostęp do metody:  
  
- Ograniczenie zakresu ułatwień dostępu do klasy, zestaw lub klasach pochodnych, jeśli może być zaufane. Jest to najprostszy sposób, aby ograniczyć dostęp do metody. Należy zauważyć, że ogólnie rzecz biorąc, klasy pochodne może być mniej wiarygodny niż klasa, z którego pochodzą one od, chociaż w niektórych przypadkach współużytkują one tożsamości klasy nadrzędnej. W szczególności są rozpoznawane przez relację zaufania z słowa kluczowego **chronione**, które nie jest koniecznie używane w kontekście zabezpieczeń.  
  
- Ograniczyć dostęp do metody wywołań określonej tożsamości — zasadniczo dowolnego określonego [dowód](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silnej nazwy, wydawcy, strefy i tak dalej) wybierz.  
  
- Ograniczyć dostęp do metody dla kodu wywołującego, niezależnie od uprawnień, możesz wybrać.  
  
 Podobnie zabezpieczenia deklaratywne pozwala na kontrolowanie dziedziczenia klas. Możesz użyć **InheritanceDemand** wykonać następujące czynności:  
  
- Wymagaj klasy pochodne, aby mieć uprawnienie lub określonej tożsamości.  
  
- Wymagaj klas pochodnych, które zastępują konkretnych metod do określonej tożsamości lub uprawnień.  
  
 Poniższy przykład pokazuje, jak chronić klasę publiczną ograniczony dostęp poprzez wymaganie, aby obiekty wywołujące były podpisane przy użyciu określonej silnej nazwy. W tym przykładzie użyto <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> z **żądanie** dla silnej nazwy. Oparta na zadaniach informacji na temat podpisać zestaw silną nazwą, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
 Użyj deklaracji przedstawione w tej sekcji, aby uniemożliwić określonej klasy i metody, jak również właściwości i zdarzenia, używany przez częściowo zaufany kod. Stosując te deklaracje do klasy, zabezpieczać do jego metod, właściwości i zdarzeń; należy jednak zauważyć, że dostęp do pola nie są stosowane zabezpieczenia deklaratywne. Należy zauważyć, że zapotrzebowanie na łącza pomoże zapewnić ochronę przed tylko bezpośredniego wywoływania i nadal może podlegać zapewnienia ataków.  
  
> [!NOTE]
>  Nowy model przejrzystości został wprowadzony w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modelu identyfikuje bezpiecznego kodu za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu. Kod zabezpieczenia krytyczny wymaga obiektów wywołujących i obiektów dziedziczących jako w pełni zaufane. Zestawy, które są uruchomione w ramach zasad zabezpieczeń dostępu kodu z wcześniejszych wersji systemu .NET Framework, można wywołać zestawy poziomu 2. W tym przypadku zabezpieczenia krytyczny atrybuty są traktowane jak linkdemand dla pełnego zaufania.  
  
 W zestawach o silnej nazwie [LinkDemand](../../../docs/framework/misc/link-demands.md) jest stosowany do wszystkich publicznie dostępnych metod, właściwości i zdarzenia w nim w celu ograniczenia ich użycia dla w pełni zaufanego kodu wywołującego. Aby wyłączyć tę funkcję, należy najpierw zastosować <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu. W efekcie jawnie oznaczanie klas, które mają zostać wykluczone z niezaufanych wywołujących jest niezbędne tylko w przypadku zestawy nieoznaczone lub zestawy za pomocą tego atrybutu; Możesz użyć tych deklaracji do oznaczania tam podzbiór typów, które nie są przeznaczone do niezaufanych wywołujących.  
  
 Poniższe przykłady pokazują, jak uniemożliwić klas i składowych przez niezaufany kod.  
  
 Aby uzyskać publiczny nonsealed klasy:  
  
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
  
 Zapieczętowane klasy publiczny:  
  
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
  
 Aby uzyskać publiczne klasy abstrakcyjnej:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 Aby uzyskać publiczny funkcje wirtualne:  
  
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
  
 Dla funkcji publicznych abstrakcyjnej:  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 Dla funkcji publicznych zastąpienie, gdzie klasa bazowa nie wymagają pełnego zaufania:  
  
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
  
 Dla funkcji publicznych przesłonięcia, gdzie klasy bazowej wymaga pełnego zaufania:  
  
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
  
 W przypadku publicznych interfejsów:  
  
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
>  W tej sekcji ostrzega o problem z zabezpieczeniami, podczas deklarowania metody jako `virtual` i `internal` (`Overloads` `Overridable` `Friend` w języku Visual Basic). To ostrzeżenie nie dotyczy wersji .NET Framework 1.0 i 1.1, nie ma zastosowania do nowszej wersji.  
  
 W .NET Framework w wersji 1.0 i 1.1 należy pamiętać o nuance ułatwień dostępu systemu typu podczas potwierdzania, że Twój kod jest niedostępny dla innych zestawów. Metoda, która jest zadeklarowana **wirtualnego** i **wewnętrzny** (**Overloads Overridable Friend** w języku Visual Basic) można zastąpić wpis vtable klasy nadrzędnej i mogą być używane tylko z w ramach tego samego zestawu, ponieważ jest on wewnętrzny. Jednak ułatwień dostępu dla zastępowanie jest określana przez **wirtualnego** — słowo kluczowe i może to być zastąpiona z innego zestawu, tak długo, jak ten kod ma dostęp do samej klasy. Jeśli możliwość zastąpienia stanowi problem, użyj zabezpieczenia deklaratywne, aby go naprawić lub usunąć **wirtualnego** — słowo kluczowe, jeśli nie jest bezwzględnie konieczne.  
  
 Należy pamiętać, że nawet wtedy, gdy kompilator języka uniemożliwia te zastąpienia z powodu błędu kompilacji, jest możliwe, że kod napisany za pomocą innych kompilatorów, aby zastąpić.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
