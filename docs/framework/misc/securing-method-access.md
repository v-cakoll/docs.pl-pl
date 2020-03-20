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
ms.openlocfilehash: a9e1226483eaa02dc8dc3dfb741e3df6b2985fbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181157"
---
# <a name="securing-method-access"></a>Zabezpieczanie dostępu metody
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Niektóre metody mogą nie być odpowiednie, aby umożliwić wywoływanie dowolnego niezaufanego kodu. Takie metody stwarzają kilka zagrożeń: metoda może dostarczyć pewnych ograniczonych informacji; może uwierzyć, że wszelkie przekazane do niego informacje; może nie wykonywać sprawdzania błędów w parametrach; lub z niewłaściwymi parametrami, może działać nieprawidłowo lub zrobić coś szkodliwego. Należy pamiętać o tych przypadkach i podjąć działania w celu ochrony metody.  
  
 W niektórych przypadkach może być konieczne ograniczenie metod, które nie są przeznaczone do użytku publicznego, ale nadal muszą być publiczne. Na przykład może mieć interfejs, który musi być wywoływany przez własne biblioteki DLL i dlatego musi być publiczny, ale nie chcesz udostępniać go publicznie, aby uniemożliwić klientom korzystanie z niego lub aby zapobiec złośliwemu kodowi wykorzystania punktu wejścia do składnika. Innym częstym powodem, aby ograniczyć metodę nie przeznaczone do użytku publicznego (ale musi być publiczny) jest uniknięcie konieczności dokumentowania i obsługi, co może być bardzo wewnętrzny interfejs.  
  
 Kod zarządzany oferuje kilka sposobów ograniczenia dostępu do metody:  
  
- Ogranicz zakres ułatwień dostępu do klasy, zestawu lub klas pochodnych, jeśli można im zaufać. Jest to najprostszy sposób, aby ograniczyć dostęp do metody. Należy zauważyć, że ogólnie klasy pochodne mogą być mniej wiarygodne niż klasa, z których pochodzą, chociaż w niektórych przypadkach mają wspólną tożsamość klasy nadrzędnej. W szczególności nie wyjmuj zaufania z **chronionego**słowa kluczowego, które niekoniecznie jest używane w kontekście zabezpieczeń.  
  
- Ogranicz dostęp do metody do wywołań określonej tożsamości — zasadniczo wszelkie konkretne [dowody](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silna nazwa, wydawca, strefa i tak dalej) wybrać.  
  
- Ogranicz dostęp do metody do osób wywołujących posiadających uprawnienia, które wybierzesz.  
  
 Podobnie deklaratywne zabezpieczeń pozwala kontrolować dziedziczenie klas. Za pomocą **InheritanceDemand** można wykonać następujące czynności:  
  
- Wymagaj klas pochodnych, aby mieć określoną tożsamość lub uprawnienia.  
  
- Wymagaj klas pochodnych, które zastępują określone metody, aby mieć określoną tożsamość lub uprawnienie.  
  
 W poniższym przykładzie pokazano, jak pomóc chronić klasę publiczną dla ograniczonego dostępu, wymagając, aby osoby wywołujące były podpisane za pomocą określonej silnej nazwy. W tym przykładzie <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> użyto z **żądaniem** silnej nazwy. Aby uzyskać informacje na temat sposobu podpisywania zestawu o silnej nazwie [i używania zestawów o silnych nazwach.](../../standard/assembly/create-use-strong-named.md)  
  
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
 Użyj deklaracji pokazanych w tej sekcji, aby zapobiec określonych klas i metod, a także właściwości i zdarzeń, z używane przez częściowo zaufany kod. Stosując te deklaracje do klasy, należy zastosować ochronę do wszystkich jego metod, właściwości i zdarzeń; Należy jednak pamiętać, że na dostęp do pól nie ma wpływu zabezpieczenia deklaratywne. Należy również zauważyć, że żądania łącza pomagają chronić tylko przed bezpośrednimi rozmówcami i nadal mogą być narażone na ataki zwabiające.  
  
> [!NOTE]
> Nowy model przezroczystości został wprowadzony w .NET Framework 4. [Security-Transparent Code, model poziomu 2](security-transparent-code-level-2.md) identyfikuje <xref:System.Security.SecurityCriticalAttribute> bezpieczny kod z atrybutem. Kod krytyczny dla zabezpieczeń wymaga, aby zarówno osoby wywołujące, jak i spadkobiercy byli w pełni zaufani. Zestawy, które są uruchomione w ramach reguł zabezpieczeń dostępu do kodu z wcześniejszych wersji programu .NET Framework można wywołać zestawy poziomu 2. W takim przypadku atrybuty krytyczne dla zabezpieczeń będą traktowane jako żądania łącza dla pełnego zaufania.  
  
 W zestawach o silnej nazwie [LinkDemand](link-demands.md) jest stosowany do wszystkich publicznie dostępnych metod, właściwości i zdarzeń w nich, aby ograniczyć ich użycie do w pełni zaufanych wywołań. Aby wyłączyć tę funkcję, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> należy zastosować atrybut. W związku z tym jawnie oznaczanie klas, aby wykluczyć niezaufanych wywoływania jest konieczne tylko dla niepodpisanych zestawów lub zestawów z tym atrybutem; Można użyć tych deklaracji, aby oznaczyć podzbiór typów w nich, które nie są przeznaczone dla niezaufanych wywołań.  
  
 Poniższe przykłady pokazują, jak zapobiec klasy i członków z używane przez niezaufanego kodu.  
  
 Dla publicznych klas nieuiszczonych:  
  
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
  
 Dla klas zapieczętowanych publicznych:  
  
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
  
 Dla publicznych klas abstrakcyjnych:  
  
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
  
 W przypadku publicznych funkcji wirtualnych:  
  
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
  
 Dla publicznych funkcji abstrakcyjnych:  
  
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
  
 W przypadku funkcji zastępowania publicznego, w których klasa podstawowa nie wymaga pełnego zaufania:  
  
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
  
 W przypadku funkcji zastępowania publicznego, w których klasa podstawowa wymaga pełnego zaufania:  
  
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
  
 W przypadku interfejsów publicznych:  
  
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
> W tej sekcji ostrzega się o problemie `virtual` `internal` z`Overloads` `Overridable` `Friend` zabezpieczeniami podczas deklarowania metody jako obu i (w języku Visual Basic). To ostrzeżenie dotyczy tylko programu .NET Framework w wersjach 1.0 i 1.1, nie ma zastosowania do nowszych wersji.  
  
 W .NET Framework w wersjach 1.0 i 1.1 należy pamiętać o niuansu dostępności systemu typu podczas potwierdzania, że kod jest niedostępny dla innych zestawów. Metoda, która jest zadeklarowana **wirtualna** i **wewnętrzna** **(Overloads Overridable Friend** w języku Visual Basic) może zastąpić wpis vtable klasy nadrzędnej i może być używana tylko z poziomu tego samego zestawu, ponieważ jest wewnętrzna. Jednak dostępność dla zastąpienia jest określana przez **wirtualne** słowo kluczowe i może to zostać zastąpione z innego zestawu, tak długo, jak ten kod ma dostęp do samej klasy. Jeśli możliwość zastąpienia stanowi problem, należy użyć zabezpieczeń deklaratywne, aby go naprawić lub usunąć **wirtualne** słowo kluczowe, jeśli nie jest ściśle wymagane.  
  
 Należy zauważyć, że nawet jeśli kompilator języka zapobiega tych zastąpienia z błędem kompilacji, jest możliwe dla kodu napisanego z innymi kompilatorami do zastąpienia.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
