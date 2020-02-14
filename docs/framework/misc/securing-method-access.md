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
ms.openlocfilehash: 5d083af6abc91121ebbc9554d03c635cabe2bbd9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217126"
---
# <a name="securing-method-access"></a><span data-ttu-id="29478-102">Zabezpieczanie dostępu metody</span><span class="sxs-lookup"><span data-stu-id="29478-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="29478-103">Niektóre metody mogą nie być odpowiednie, aby zezwolić na wywołanie dowolnego niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="29478-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="29478-104">Takie metody stanowią kilka zagrożeń: Metoda może zawierać pewne informacje z ograniczeniami; może ona zainteresować wszystkie informacje, które zostały do niego przesłane; Sprawdzanie błędów w parametrach może nie być możliwe. lub przy użyciu nieprawidłowych parametrów może to spowodować awarię lub wykonać coś szkodliwego.</span><span class="sxs-lookup"><span data-stu-id="29478-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="29478-105">Należy zwrócić uwagę na te przypadki i podjąć działania w celu ułatwienia ochrony metody.</span><span class="sxs-lookup"><span data-stu-id="29478-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="29478-106">W niektórych przypadkach może być konieczne ograniczenie metod, które nie są przeznaczone do użytku publicznego, ale nadal musi być publiczny.</span><span class="sxs-lookup"><span data-stu-id="29478-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="29478-107">Na przykład może istnieć interfejs, który musi być wywoływany we własnych bibliotekach DLL i dlatego musi być publiczny, ale nie chce ujawniać go publicznie, aby uniemożliwić klientom korzystanie z niego lub uniemożliwić złośliwemu kodowi wykorzystanie punktu wejścia do składnika.</span><span class="sxs-lookup"><span data-stu-id="29478-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="29478-108">Inny typowy powód ograniczenia metody nieprzeznaczonej do użytku publicznego (ale musi być publiczna) polega na tym, że należy unikać dokumentowania i obsługi tego, co może być interfejsem w bardzo wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="29478-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="29478-109">Kod zarządzany oferuje kilka sposobów ograniczenia dostępu do metody:</span><span class="sxs-lookup"><span data-stu-id="29478-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="29478-110">Ogranicz zakres dostępności do klasy, zestawu lub klas pochodnych, jeśli mogą być zaufane.</span><span class="sxs-lookup"><span data-stu-id="29478-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="29478-111">Jest to najprostszy sposób ograniczenia dostępu do metody.</span><span class="sxs-lookup"><span data-stu-id="29478-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="29478-112">Należy zauważyć, że ogólnie rzecz biorąc klasy pochodne mogą być mniej wiarygodne niż Klasa, z której pochodzi, ale w niektórych przypadkach współużytkują tożsamość klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="29478-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="29478-113">W szczególności nie należy wywnioskować zaufania z **chronionego**słowa kluczowego, które nie jest koniecznie używane w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="29478-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="29478-114">Ogranicz dostęp do metod wywołujących o określonej tożsamości — zasadniczo, wszelkich określonych [dowodów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silna nazwa, Wydawca, strefa itd.).</span><span class="sxs-lookup"><span data-stu-id="29478-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="29478-115">Ogranicz dostęp do metod wywołujących mających wybrane uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="29478-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="29478-116">Podobnie Zabezpieczenia deklaracyjne umożliwiają kontrolowanie dziedziczenia klas.</span><span class="sxs-lookup"><span data-stu-id="29478-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="29478-117">Możesz użyć **InheritanceDemand** , aby wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="29478-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="29478-118">Wymagaj, aby klasy pochodne miały określoną tożsamość lub uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="29478-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="29478-119">Wymagaj klas pochodnych, które zastępują określone metody, aby mieć określoną tożsamość lub uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="29478-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="29478-120">Poniższy przykład pokazuje, jak zabezpieczyć klasę publiczną dla ograniczonego dostępu przez wymaganie, aby obiekty wywołujące były podpisane przy użyciu określonej silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="29478-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="29478-121">Ten przykład używa <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> z **zapotrzebowaniem** na silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="29478-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="29478-122">Informacje na temat sposobu podpisywania zestawu o silnej nazwie można znaleźć w temacie [Tworzenie i używanie zestawów o silnej nazwie](../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="29478-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="29478-123">Wyłączanie klas i członków z zasobów używanych przez niezaufany kod</span><span class="sxs-lookup"><span data-stu-id="29478-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="29478-124">Użyj deklaracji przedstawionych w tej sekcji, aby zapobiec używaniu określonych klas i metod, a także właściwości i zdarzeń, z których korzysta kod częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="29478-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="29478-125">Stosując te deklaracje do klasy, stosuje się ochronę do wszystkich metod, właściwości i zdarzeń; należy jednak pamiętać, że zabezpieczenia deklaracyjne nie wpływają na dostęp do pola.</span><span class="sxs-lookup"><span data-stu-id="29478-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="29478-126">Należy również pamiętać, że wymagania dotyczące linków pomagają chronić przed bezpośrednimi wywołaniami i nadal mogą być objęte atakami luring.</span><span class="sxs-lookup"><span data-stu-id="29478-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29478-127">Nowy model przezroczystości został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="29478-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="29478-128">[Kod poziomu przezroczystego zabezpieczeń, model Level 2](security-transparent-code-level-2.md) identyfikuje bezpieczny kod z atrybutem <xref:System.Security.SecurityCriticalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="29478-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="29478-129">Kod krytyczny dla bezpieczeństwa wymaga, aby zarówno obiekty wywołujące, jak i dziedziczące, były w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="29478-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="29478-130">Zestawy, które są uruchomione w ramach reguł zabezpieczeń dostępu kodu z wcześniejszych wersji .NET Framework, mogą wywoływać zestawy poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="29478-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="29478-131">W takim przypadku atrybuty krytyczne dla zabezpieczeń będą traktowane jako żądania połączeń dla pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="29478-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="29478-132">W zestawach o silnej nazwie [LinkDemand](link-demands.md) jest stosowana do wszystkich publicznie dostępnych metod, właściwości i zdarzeń w tym miejscu, aby ograniczyć ich użycie do w pełni zaufanych wywołujących.</span><span class="sxs-lookup"><span data-stu-id="29478-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="29478-133">Aby wyłączyć tę funkcję, należy zastosować atrybut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>.</span><span class="sxs-lookup"><span data-stu-id="29478-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="29478-134">W ten sposób jawne oznaczanie klas do wykluczenia niezaufanych wywołujących jest niezbędne tylko dla niepodpisanych zestawów lub zestawów z tym atrybutem; za pomocą tych deklaracji można oznaczyć podzbiór typów, które nie są przeznaczone dla niezaufanych obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="29478-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="29478-135">W poniższych przykładach pokazano, jak zapobiegać używaniu klas i elementów członkowskich przez niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="29478-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="29478-136">Dla publicznych niezapieczętowanych klas:</span><span class="sxs-lookup"><span data-stu-id="29478-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="29478-137">Dla publicznych klas zapieczętowanych:</span><span class="sxs-lookup"><span data-stu-id="29478-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="29478-138">Dla publicznych klas abstrakcyjnych:</span><span class="sxs-lookup"><span data-stu-id="29478-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="29478-139">Dla publicznych funkcji wirtualnych:</span><span class="sxs-lookup"><span data-stu-id="29478-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="29478-140">W przypadku publicznych funkcji abstrakcyjnych:</span><span class="sxs-lookup"><span data-stu-id="29478-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="29478-141">W przypadku funkcji przesłania publicznego, w których Klasa bazowa nie wymaga pełnego zaufania:</span><span class="sxs-lookup"><span data-stu-id="29478-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="29478-142">W przypadku funkcji przesłania publicznego, w których Klasa bazowa wymaga pełnego zaufania:</span><span class="sxs-lookup"><span data-stu-id="29478-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="29478-143">Dla interfejsów publicznych:</span><span class="sxs-lookup"><span data-stu-id="29478-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="29478-144">Wirtualne wewnętrzne zastąpienia lub przeciążenia zastępowanego przyjaciela klasy</span><span class="sxs-lookup"><span data-stu-id="29478-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29478-145">Ta sekcja ostrzega o problemie z zabezpieczeniami podczas deklarowania metody zarówno `virtual`, jak i `internal` (`Overloads` `Overridable` `Friend` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="29478-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="29478-146">To ostrzeżenie dotyczy tylko .NET Framework wersji 1,0 i 1,1, nie ma zastosowania do nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="29478-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="29478-147">W .NET Framework wersje 1,0 i 1,1 należy mieć świadomość Nuance o dostępności systemu typu w przypadku potwierdzenia, że kod jest niedostępny dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="29478-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="29478-148">Metoda, która jest zadeklarowana jako **wirtualna** i **wewnętrzna** (**overloads zaprzyjaźniony przyjaciel** w Visual Basic), może przesłonić wpis w tabeli przestawnej klasy nadrzędnej i może być używana tylko z tego samego zestawu, ponieważ jest ona wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="29478-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="29478-149">Jednak dostępność dla przesłaniania jest określana przez **wirtualne** słowo kluczowe i można ją zastąpić z innego zestawu, o ile ten kod ma dostęp do samej klasy.</span><span class="sxs-lookup"><span data-stu-id="29478-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="29478-150">Jeśli w wyniku przesłonięcia wystąpi problem, Użyj zabezpieczeń deklaratywnych, aby je usunąć, lub Usuń słowo kluczowe **Virtual** , jeśli nie jest to absolutnie wymagane.</span><span class="sxs-lookup"><span data-stu-id="29478-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="29478-151">Należy zauważyć, że nawet jeśli kompilator języka uniemożliwia te zastąpienia z błędem kompilacji, możliwe jest użycie kodu pisanego z innymi kompilatorami do przesłonięcia.</span><span class="sxs-lookup"><span data-stu-id="29478-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29478-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29478-152">See also</span></span>

- [<span data-ttu-id="29478-153">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="29478-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
