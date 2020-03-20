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
# <a name="securing-method-access"></a><span data-ttu-id="b3fba-102">Zabezpieczanie dostępu metody</span><span class="sxs-lookup"><span data-stu-id="b3fba-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="b3fba-103">Niektóre metody mogą nie być odpowiednie, aby umożliwić wywoływanie dowolnego niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="b3fba-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="b3fba-104">Takie metody stwarzają kilka zagrożeń: metoda może dostarczyć pewnych ograniczonych informacji; może uwierzyć, że wszelkie przekazane do niego informacje; może nie wykonywać sprawdzania błędów w parametrach; lub z niewłaściwymi parametrami, może działać nieprawidłowo lub zrobić coś szkodliwego.</span><span class="sxs-lookup"><span data-stu-id="b3fba-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="b3fba-105">Należy pamiętać o tych przypadkach i podjąć działania w celu ochrony metody.</span><span class="sxs-lookup"><span data-stu-id="b3fba-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="b3fba-106">W niektórych przypadkach może być konieczne ograniczenie metod, które nie są przeznaczone do użytku publicznego, ale nadal muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="b3fba-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="b3fba-107">Na przykład może mieć interfejs, który musi być wywoływany przez własne biblioteki DLL i dlatego musi być publiczny, ale nie chcesz udostępniać go publicznie, aby uniemożliwić klientom korzystanie z niego lub aby zapobiec złośliwemu kodowi wykorzystania punktu wejścia do składnika.</span><span class="sxs-lookup"><span data-stu-id="b3fba-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="b3fba-108">Innym częstym powodem, aby ograniczyć metodę nie przeznaczone do użytku publicznego (ale musi być publiczny) jest uniknięcie konieczności dokumentowania i obsługi, co może być bardzo wewnętrzny interfejs.</span><span class="sxs-lookup"><span data-stu-id="b3fba-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="b3fba-109">Kod zarządzany oferuje kilka sposobów ograniczenia dostępu do metody:</span><span class="sxs-lookup"><span data-stu-id="b3fba-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="b3fba-110">Ogranicz zakres ułatwień dostępu do klasy, zestawu lub klas pochodnych, jeśli można im zaufać.</span><span class="sxs-lookup"><span data-stu-id="b3fba-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="b3fba-111">Jest to najprostszy sposób, aby ograniczyć dostęp do metody.</span><span class="sxs-lookup"><span data-stu-id="b3fba-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="b3fba-112">Należy zauważyć, że ogólnie klasy pochodne mogą być mniej wiarygodne niż klasa, z których pochodzą, chociaż w niektórych przypadkach mają wspólną tożsamość klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b3fba-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="b3fba-113">W szczególności nie wyjmuj zaufania z **chronionego**słowa kluczowego, które niekoniecznie jest używane w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b3fba-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="b3fba-114">Ogranicz dostęp do metody do wywołań określonej tożsamości — zasadniczo wszelkie konkretne [dowody](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silna nazwa, wydawca, strefa i tak dalej) wybrać.</span><span class="sxs-lookup"><span data-stu-id="b3fba-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="b3fba-115">Ogranicz dostęp do metody do osób wywołujących posiadających uprawnienia, które wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="b3fba-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="b3fba-116">Podobnie deklaratywne zabezpieczeń pozwala kontrolować dziedziczenie klas.</span><span class="sxs-lookup"><span data-stu-id="b3fba-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="b3fba-117">Za pomocą **InheritanceDemand** można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b3fba-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="b3fba-118">Wymagaj klas pochodnych, aby mieć określoną tożsamość lub uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b3fba-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="b3fba-119">Wymagaj klas pochodnych, które zastępują określone metody, aby mieć określoną tożsamość lub uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="b3fba-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="b3fba-120">W poniższym przykładzie pokazano, jak pomóc chronić klasę publiczną dla ograniczonego dostępu, wymagając, aby osoby wywołujące były podpisane za pomocą określonej silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b3fba-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="b3fba-121">W tym przykładzie <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> użyto z **żądaniem** silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b3fba-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="b3fba-122">Aby uzyskać informacje na temat sposobu podpisywania zestawu o silnej nazwie [i używania zestawów o silnych nazwach.](../../standard/assembly/create-use-strong-named.md)</span><span class="sxs-lookup"><span data-stu-id="b3fba-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="b3fba-123">Wyłączanie klas i członków z zasobów używanych przez niezaufany kod</span><span class="sxs-lookup"><span data-stu-id="b3fba-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="b3fba-124">Użyj deklaracji pokazanych w tej sekcji, aby zapobiec określonych klas i metod, a także właściwości i zdarzeń, z używane przez częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="b3fba-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="b3fba-125">Stosując te deklaracje do klasy, należy zastosować ochronę do wszystkich jego metod, właściwości i zdarzeń; Należy jednak pamiętać, że na dostęp do pól nie ma wpływu zabezpieczenia deklaratywne.</span><span class="sxs-lookup"><span data-stu-id="b3fba-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="b3fba-126">Należy również zauważyć, że żądania łącza pomagają chronić tylko przed bezpośrednimi rozmówcami i nadal mogą być narażone na ataki zwabiające.</span><span class="sxs-lookup"><span data-stu-id="b3fba-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3fba-127">Nowy model przezroczystości został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b3fba-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="b3fba-128">[Security-Transparent Code, model poziomu 2](security-transparent-code-level-2.md) identyfikuje <xref:System.Security.SecurityCriticalAttribute> bezpieczny kod z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="b3fba-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="b3fba-129">Kod krytyczny dla zabezpieczeń wymaga, aby zarówno osoby wywołujące, jak i spadkobiercy byli w pełni zaufani.</span><span class="sxs-lookup"><span data-stu-id="b3fba-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="b3fba-130">Zestawy, które są uruchomione w ramach reguł zabezpieczeń dostępu do kodu z wcześniejszych wersji programu .NET Framework można wywołać zestawy poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="b3fba-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="b3fba-131">W takim przypadku atrybuty krytyczne dla zabezpieczeń będą traktowane jako żądania łącza dla pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="b3fba-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="b3fba-132">W zestawach o silnej nazwie [LinkDemand](link-demands.md) jest stosowany do wszystkich publicznie dostępnych metod, właściwości i zdarzeń w nich, aby ograniczyć ich użycie do w pełni zaufanych wywołań.</span><span class="sxs-lookup"><span data-stu-id="b3fba-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="b3fba-133">Aby wyłączyć tę funkcję, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> należy zastosować atrybut.</span><span class="sxs-lookup"><span data-stu-id="b3fba-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="b3fba-134">W związku z tym jawnie oznaczanie klas, aby wykluczyć niezaufanych wywoływania jest konieczne tylko dla niepodpisanych zestawów lub zestawów z tym atrybutem; Można użyć tych deklaracji, aby oznaczyć podzbiór typów w nich, które nie są przeznaczone dla niezaufanych wywołań.</span><span class="sxs-lookup"><span data-stu-id="b3fba-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="b3fba-135">Poniższe przykłady pokazują, jak zapobiec klasy i członków z używane przez niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="b3fba-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="b3fba-136">Dla publicznych klas nieuiszczonych:</span><span class="sxs-lookup"><span data-stu-id="b3fba-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-137">Dla klas zapieczętowanych publicznych:</span><span class="sxs-lookup"><span data-stu-id="b3fba-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-138">Dla publicznych klas abstrakcyjnych:</span><span class="sxs-lookup"><span data-stu-id="b3fba-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-139">W przypadku publicznych funkcji wirtualnych:</span><span class="sxs-lookup"><span data-stu-id="b3fba-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-140">Dla publicznych funkcji abstrakcyjnych:</span><span class="sxs-lookup"><span data-stu-id="b3fba-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-141">W przypadku funkcji zastępowania publicznego, w których klasa podstawowa nie wymaga pełnego zaufania:</span><span class="sxs-lookup"><span data-stu-id="b3fba-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-142">W przypadku funkcji zastępowania publicznego, w których klasa podstawowa wymaga pełnego zaufania:</span><span class="sxs-lookup"><span data-stu-id="b3fba-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="b3fba-143">W przypadku interfejsów publicznych:</span><span class="sxs-lookup"><span data-stu-id="b3fba-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="b3fba-144">Wirtualne wewnętrzne zastąpienia lub przeciążenia zastępowanego przyjaciela klasy</span><span class="sxs-lookup"><span data-stu-id="b3fba-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3fba-145">W tej sekcji ostrzega się o problemie `virtual` `internal` z`Overloads` `Overridable` `Friend` zabezpieczeniami podczas deklarowania metody jako obu i (w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b3fba-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="b3fba-146">To ostrzeżenie dotyczy tylko programu .NET Framework w wersjach 1.0 i 1.1, nie ma zastosowania do nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="b3fba-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="b3fba-147">W .NET Framework w wersjach 1.0 i 1.1 należy pamiętać o niuansu dostępności systemu typu podczas potwierdzania, że kod jest niedostępny dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="b3fba-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="b3fba-148">Metoda, która jest zadeklarowana **wirtualna** i **wewnętrzna** **(Overloads Overridable Friend** w języku Visual Basic) może zastąpić wpis vtable klasy nadrzędnej i może być używana tylko z poziomu tego samego zestawu, ponieważ jest wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="b3fba-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="b3fba-149">Jednak dostępność dla zastąpienia jest określana przez **wirtualne** słowo kluczowe i może to zostać zastąpione z innego zestawu, tak długo, jak ten kod ma dostęp do samej klasy.</span><span class="sxs-lookup"><span data-stu-id="b3fba-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="b3fba-150">Jeśli możliwość zastąpienia stanowi problem, należy użyć zabezpieczeń deklaratywne, aby go naprawić lub usunąć **wirtualne** słowo kluczowe, jeśli nie jest ściśle wymagane.</span><span class="sxs-lookup"><span data-stu-id="b3fba-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="b3fba-151">Należy zauważyć, że nawet jeśli kompilator języka zapobiega tych zastąpienia z błędem kompilacji, jest możliwe dla kodu napisanego z innymi kompilatorami do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="b3fba-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fba-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3fba-152">See also</span></span>

- [<span data-ttu-id="b3fba-153">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="b3fba-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
