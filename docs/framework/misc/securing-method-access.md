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
ms.openlocfilehash: e981d75ead5ec2e7f95a854da8c0fa42f476d9da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910787"
---
# <a name="securing-method-access"></a>Zabezpieczanie dostępu metody
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Niektóre metody mogą nie być odpowiednie, aby zezwolić na wywołanie dowolnego niezaufanego kodu. Takie metody stwarzają kilka zagrożeń: Metoda może udostępniać pewne informacje z ograniczeniami; może ona zainteresować wszystkie informacje, które zostały do niego przesłane; Sprawdzanie błędów w parametrach może nie być możliwe. lub przy użyciu nieprawidłowych parametrów może to spowodować awarię lub wykonać coś szkodliwego. Należy zwrócić uwagę na te przypadki i podjąć działania w celu ułatwienia ochrony metody.  
  
 W niektórych przypadkach może być konieczne ograniczenie metod, które nie są przeznaczone do użytku publicznego, ale nadal musi być publiczny. Na przykład może istnieć interfejs, który musi być wywoływany we własnych bibliotekach DLL i dlatego musi być publiczny, ale nie chce ujawniać go publicznie, aby uniemożliwić klientom korzystanie z niego lub uniemożliwić złośliwemu kodowi wykorzystanie punktu wejścia do składnika. Inny typowy powód ograniczenia metody nieprzeznaczonej do użytku publicznego (ale musi być publiczna) polega na tym, że należy unikać dokumentowania i obsługi tego, co może być interfejsem w bardzo wewnętrznym.  
  
 Kod zarządzany oferuje kilka sposobów ograniczenia dostępu do metody:  
  
- Ogranicz zakres dostępności do klasy, zestawu lub klas pochodnych, jeśli mogą być zaufane. Jest to najprostszy sposób ograniczenia dostępu do metody. Należy zauważyć, że ogólnie rzecz biorąc klasy pochodne mogą być mniej wiarygodne niż Klasa, z której pochodzi, ale w niektórych przypadkach współużytkują tożsamość klasy nadrzędnej. W szczególności nie należy wywnioskować zaufania z **chronionego**słowa kluczowego, które nie jest koniecznie używane w kontekście zabezpieczeń.  
  
- Ogranicz dostęp do metod wywołujących o określonej tożsamości — zasadniczo, wszelkich określonych [dowodów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silna nazwa, Wydawca, strefa itd.).  
  
- Ogranicz dostęp do metod wywołujących mających wybrane uprawnienia.  
  
 Podobnie Zabezpieczenia deklaracyjne umożliwiają kontrolowanie dziedziczenia klas. Możesz użyć **InheritanceDemand** , aby wykonać następujące czynności:  
  
- Wymagaj, aby klasy pochodne miały określoną tożsamość lub uprawnienie.  
  
- Wymagaj klas pochodnych, które zastępują określone metody, aby mieć określoną tożsamość lub uprawnienie.  
  
 Poniższy przykład pokazuje, jak zabezpieczyć klasę publiczną dla ograniczonego dostępu przez wymaganie, aby obiekty wywołujące były podpisane przy użyciu określonej silnej nazwy. W tym przykładzie jest <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> stosowane **żądanie** o silnej nazwie. Informacje na temat sposobu podpisywania zestawu o silnej nazwie można znaleźć w temacie [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
 Użyj deklaracji przedstawionych w tej sekcji, aby zapobiec używaniu określonych klas i metod, a także właściwości i zdarzeń, z których korzysta kod częściowo zaufany. Stosując te deklaracje do klasy, stosuje się ochronę do wszystkich metod, właściwości i zdarzeń; należy jednak pamiętać, że zabezpieczenia deklaracyjne nie wpływają na dostęp do pola. Należy również pamiętać, że wymagania dotyczące linków pomagają chronić przed bezpośrednimi wywołaniami i nadal mogą być objęte atakami luring.  
  
> [!NOTE]
> Nowy model przezroczystości został wprowadzony w .NET Framework 4. [Kod poziomu przezroczystego zabezpieczeń, model Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) identyfikuje bezpieczny kod z <xref:System.Security.SecurityCriticalAttribute> atrybutem. Kod krytyczny dla bezpieczeństwa wymaga, aby zarówno obiekty wywołujące, jak i dziedziczące, były w pełni zaufane. Zestawy, które są uruchomione w ramach reguł zabezpieczeń dostępu kodu z wcześniejszych wersji .NET Framework, mogą wywoływać zestawy poziomu 2. W takim przypadku atrybuty krytyczne dla zabezpieczeń będą traktowane jako żądania połączeń dla pełnego zaufania.  
  
 W zestawach o silnej nazwie [LinkDemand](../../../docs/framework/misc/link-demands.md) jest stosowana do wszystkich publicznie dostępnych metod, właściwości i zdarzeń w tym miejscu, aby ograniczyć ich użycie do w pełni zaufanych wywołujących. Aby wyłączyć tę funkcję, należy zastosować <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybut. W ten sposób jawne oznaczanie klas do wykluczenia niezaufanych wywołujących jest niezbędne tylko dla niepodpisanych zestawów lub zestawów z tym atrybutem; za pomocą tych deklaracji można oznaczyć podzbiór typów, które nie są przeznaczone dla niezaufanych obiektów wywołujących.  
  
 W poniższych przykładach pokazano, jak zapobiegać używaniu klas i elementów członkowskich przez niezaufany kod.  
  
 Dla publicznych niezapieczętowanych klas:  
  
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
  
 Dla publicznych klas zapieczętowanych:  
  
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
  
 W przypadku publicznych funkcji abstrakcyjnych:  
  
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
  
 W przypadku funkcji przesłania publicznego, w których Klasa bazowa nie wymaga pełnego zaufania:  
  
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
  
 W przypadku funkcji przesłania publicznego, w których Klasa bazowa wymaga pełnego zaufania:  
  
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
  
 Dla interfejsów publicznych:  
  
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
> Ta sekcja ostrzega o problemach z zabezpieczeniami podczas `virtual` deklarowania metody jako i `internal` (`Overloads` `Overridable` `Friend` w Visual Basic). To ostrzeżenie dotyczy tylko .NET Framework wersji 1,0 i 1,1, nie ma zastosowania do nowszych wersji.  
  
 W .NET Framework wersje 1,0 i 1,1 należy mieć świadomość Nuance o dostępności systemu typu w przypadku potwierdzenia, że kod jest niedostępny dla innych zestawów. Metoda, która jest zadeklarowana jako **wirtualna** i **wewnętrzna** (**overloads zaprzyjaźniony przyjaciel** w Visual Basic), może przesłonić wpis w tabeli przestawnej klasy nadrzędnej i może być używana tylko z tego samego zestawu, ponieważ jest ona wewnętrzna. Jednak dostępność dla przesłaniania jest określana przez **wirtualne** słowo kluczowe i można ją zastąpić z innego zestawu, o ile ten kod ma dostęp do samej klasy. Jeśli w wyniku przesłonięcia wystąpi problem, Użyj zabezpieczeń deklaratywnych, aby je usunąć, lub Usuń słowo kluczowe **Virtual** , jeśli nie jest to absolutnie wymagane.  
  
 Należy zauważyć, że nawet jeśli kompilator języka uniemożliwia te zastąpienia z błędem kompilacji, możliwe jest użycie kodu pisanego z innymi kompilatorami do przesłonięcia.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
