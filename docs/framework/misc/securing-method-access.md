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
ms.openlocfilehash: b0d9ddbd6c7b027a7c342f4c14192a7571beb592
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="securing-method-access"></a><span data-ttu-id="2f90f-102">Zabezpieczanie dostępu metody</span><span class="sxs-lookup"><span data-stu-id="2f90f-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="2f90f-103">W przypadku niektórych metod może nie nadawać się do dowolnego kodu niezaufanej do wywołania.</span><span class="sxs-lookup"><span data-stu-id="2f90f-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="2f90f-104">Takie metody stanowić zagrożenie kilka: metoda może zawierać niektórych ograniczone informacje; może być podejrzeń wszelkie informacje przekazywane może nie sprawdzanie błędów dla parametrów; lub z niewłaściwego parametrami, może być nieprawidłowe działanie lub czymś szkodliwe.</span><span class="sxs-lookup"><span data-stu-id="2f90f-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="2f90f-105">Należy należy pamiętać o tych przypadkach i podjąć działania w celu ochrony metody.</span><span class="sxs-lookup"><span data-stu-id="2f90f-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="2f90f-106">W niektórych przypadkach może być konieczne ograniczanie metod, które nie są przeznaczone do użytku publicznego, ale nadal muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="2f90f-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="2f90f-107">Na przykład może być interfejs, który musi być wywoływany przez własnych bibliotek DLL i dlatego muszą być publiczne, ale nie chcesz udostępnić go publicznie, aby uniemożliwić klientom korzystanie z niego lub aby uniemożliwić wykorzystanie punktem wejścia do składnika złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="2f90f-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="2f90f-108">Kolejny powód wspólnej do ograniczania metody nie przeznaczony do użytku publicznego (ale który muszą być publiczne) jest, aby uniknąć konieczności dokumentów i obsługi, co może być bardzo wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="2f90f-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="2f90f-109">Zarządzany kod oferuje kilka sposobów do ograniczania dostępu do metody:</span><span class="sxs-lookup"><span data-stu-id="2f90f-109">Managed code offers several ways to restrict method access:</span></span>  
  
-   <span data-ttu-id="2f90f-110">Ograniczenie zakresu ułatwień dostępu do klasy, zestawu lub klasy pochodne, jeśli może być zaufane.</span><span class="sxs-lookup"><span data-stu-id="2f90f-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="2f90f-111">Jest to najprostszy sposób, aby ograniczyć dostęp do metody.</span><span class="sxs-lookup"><span data-stu-id="2f90f-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="2f90f-112">Należy pamiętać, że klasy pochodne — ogólnie rzecz biorąc, może być mniej zaufanego niż klasa, które pochodzą one od, chociaż w niektórych przypadkach mają tożsamości klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2f90f-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="2f90f-113">W szczególności nie wnioskować zaufanie od słowa kluczowego **chronione**, który nie jest zawsze używany w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2f90f-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
-   <span data-ttu-id="2f90f-114">Ograniczenia dostępu metody wywołań określoną tożsamością — zasadniczo żadnych określonego [dowód](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (silnej nazwy, wydawcy strefy i tak dalej) wybierz.</span><span class="sxs-lookup"><span data-stu-id="2f90f-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
-   <span data-ttu-id="2f90f-115">Ograniczenia dostępu metody dotyczące obiektów wywołujących uzyskanie niezależnie od uprawnień, należy wybrać.</span><span class="sxs-lookup"><span data-stu-id="2f90f-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="2f90f-116">Podobnie zabezpieczenia deklaratywne pozwala na kontrolowanie dziedziczenia klas.</span><span class="sxs-lookup"><span data-stu-id="2f90f-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="2f90f-117">Można użyć **InheritanceDemand** wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2f90f-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
-   <span data-ttu-id="2f90f-118">Wymagaj klas pochodnych określona tożsamość lub uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="2f90f-118">Require derived classes to have a specified identity or permission.</span></span>  
  
-   <span data-ttu-id="2f90f-119">Wymagaj klas pochodnych przesłaniające konkretnych metod określona tożsamość lub uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="2f90f-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="2f90f-120">Poniższy przykład pokazuje, jak w celu ochrony klasą publiczną ograniczony dostęp przez wymaganie, aby obiekty wywołujące były podpisane przy użyciu określonego silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2f90f-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="2f90f-121">W tym przykładzie użyto <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> z **żądanie** silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2f90f-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="2f90f-122">Oparty na zadaniach informacji na temat podpisać zestaw o silnej nazwie, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2f90f-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="2f90f-123">Wyłączanie klas i członków z zasobów używanych przez niezaufany kod</span><span class="sxs-lookup"><span data-stu-id="2f90f-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="2f90f-124">Użyj deklaracji w tej sekcji, aby zapobiec używany przez kod częściowo zaufany określonej klasy i metody, jak również właściwości i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2f90f-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="2f90f-125">Stosując deklaracji klasy, stosują ochronę do jego metod, właściwości i zdarzeń; jednak należy pamiętać, że dostęp do pola nie ma wpływu na zabezpieczenia deklaratywne.</span><span class="sxs-lookup"><span data-stu-id="2f90f-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="2f90f-126">Należy też zauważyć, że linkdemand pomoże zapewnić ochronę przed tylko bezpośredniego wywoływania i nadal mogą być narażone na ataki zapewnienia.</span><span class="sxs-lookup"><span data-stu-id="2f90f-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f90f-127">Wprowadzono nowy model przezroczystość w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f90f-127">A new transparency model has been introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="2f90f-128">[Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modelu identyfikuje bezpieczny kod z <xref:System.Security.SecurityCriticalAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2f90f-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="2f90f-129">Kod krytyczny dla zabezpieczeń wymaga zarówno wywołań i dziedziczenia, mogą być w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="2f90f-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="2f90f-130">Zestawy, które działają w ramach zasad zabezpieczeń dostępu kodu z wcześniejszych wersji .NET Framework mogą wywoływać zestawy poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="2f90f-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="2f90f-131">W takim przypadku atrybuty krytyczny dla zabezpieczeń będą traktowane jako linkdemand dla pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="2f90f-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="2f90f-132">W zestawy o silnych nazwach [LinkDemand](../../../docs/framework/misc/link-demands.md) jest stosowany do wszystkich publicznie dostępnych metod, właściwości i zdarzenia tam, aby ograniczyć ich stosowania do wywoływania w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="2f90f-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="2f90f-133">Aby wyłączyć tę funkcję, należy zastosować <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2f90f-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="2f90f-134">W związku z tym jawnie oznaczenie klasy do wykluczenia niezaufanych obiektów wywołujących jest niezbędne tylko w przypadku zestawy nieoznaczone lub zestawów z tym atrybutem; Możesz użyć tych deklaracjach tam zaznaczania podzbiór typy, które nie są przeznaczone do wywoływania w niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="2f90f-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="2f90f-135">Poniższe przykłady przedstawiają sposób uniemożliwiać korzystanie w kodzie niezaufanym klas i członków.</span><span class="sxs-lookup"><span data-stu-id="2f90f-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="2f90f-136">Dla klas publicznych nonsealed:</span><span class="sxs-lookup"><span data-stu-id="2f90f-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-137">Dla publicznego zapieczętowane klasy:</span><span class="sxs-lookup"><span data-stu-id="2f90f-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-138">Dla publicznych klasy abstrakcyjne:</span><span class="sxs-lookup"><span data-stu-id="2f90f-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-139">Dla publicznych funkcji wirtualnych:</span><span class="sxs-lookup"><span data-stu-id="2f90f-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-140">Dla publicznych funkcje abstrakcyjne:</span><span class="sxs-lookup"><span data-stu-id="2f90f-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-141">Dla funkcji publicznego zastąpienie, gdzie klasy podstawowej nie wymaga pełnego zaufania:</span><span class="sxs-lookup"><span data-stu-id="2f90f-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-142">Dla funkcji zastąpienie publicznych gdzie klasa podstawowa wymaga pełnego zaufania:</span><span class="sxs-lookup"><span data-stu-id="2f90f-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="2f90f-143">Interfejsów publicznych:</span><span class="sxs-lookup"><span data-stu-id="2f90f-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="2f90f-144">Wirtualne wewnętrzne zastąpienia lub przeciążenia zastępowanego przyjaciela klasy</span><span class="sxs-lookup"><span data-stu-id="2f90f-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f90f-145">W tej sekcji ostrzega o problem z zabezpieczeniami przy deklarowaniu metody jednocześnie jako `virtual` i `internal` (`Overloads``Overridable``Friend` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2f90f-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads``Overridable``Friend` in Visual Basic).</span></span> <span data-ttu-id="2f90f-146">To ostrzeżenie nie dotyczy wersji systemu .NET Framework 1.0 i 1.1, nie ma zastosowania do nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="2f90f-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="2f90f-147">W wersji systemu .NET Framework 1.0 i 1.1 należy pamiętać o nuance ułatwień dostępu systemu typu po potwierdzeniu, że kod jest niedostępne dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="2f90f-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="2f90f-148">Metoda, która jest zadeklarowana jako **wirtualnego** i **wewnętrzny** (**Overloads możliwym do zastąpienia Friend** w języku Visual Basic) można zastąpić wpis vtable klasy nadrzędnej i mogą być używane tylko z w ramach tego samego zestawu, ponieważ jest on wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="2f90f-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="2f90f-149">Jednak ułatwień dostępu dla zastępowanie jest określany przez **wirtualnego** — słowo kluczowe, a to może zostać zastąpiona z innego zestawu, pod warunkiem, że kod ma dostęp do samej klasy.</span><span class="sxs-lookup"><span data-stu-id="2f90f-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="2f90f-150">Jeśli możliwość zastąpienia stanowi problem, użyj zabezpieczenia deklaratywne, aby go rozwiązać, lub usuń **wirtualnego** — słowo kluczowe, jeśli nie jest ścisłym wymogiem.</span><span class="sxs-lookup"><span data-stu-id="2f90f-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="2f90f-151">Należy pamiętać, że nawet jeśli kompilatora języka uniemożliwia zastąpienia z powodu błędu kompilacji, możliwe kod napisany za pomocą inne kompilatory do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="2f90f-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f90f-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f90f-152">See Also</span></span>  
 [<span data-ttu-id="2f90f-153">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="2f90f-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
