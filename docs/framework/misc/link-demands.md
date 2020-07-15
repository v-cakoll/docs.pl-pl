---
title: Żądania połączeń
description: Przeczytaj informacje o zapotrzebowaniu na łącza, które powodują sprawdzanie zabezpieczeń w kompilacji "just-in-Time" (JIT) i sprawdzaj tylko natychmiastowy zestaw kodu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: eaf9ee1bb5cd10c724240bacac014503685a0c8c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309108"
---
# <a name="link-demands"></a><span data-ttu-id="24fec-103">Żądania połączeń</span><span class="sxs-lookup"><span data-stu-id="24fec-103">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="24fec-104">Żądanie linku powoduje sprawdzenie zabezpieczeń podczas kompilacji just-in-Time i sprawdza tylko bezpośrednio wywołujący zestaw kodu.</span><span class="sxs-lookup"><span data-stu-id="24fec-104">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="24fec-105">Łączenie występuje, gdy kod jest powiązany z odwołaniem do typu, w tym odwołaniami wskaźników funkcji i wywołaniami metod.</span><span class="sxs-lookup"><span data-stu-id="24fec-105">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="24fec-106">Jeśli zestaw wywołujący nie ma wystarczających uprawnień do łączenia się z kodem, link jest niedozwolony i podczas ładowania i uruchamiania kodu zostanie wygenerowany wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="24fec-106">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="24fec-107">Wymagania dotyczące linków można przesłonić w klasach, które dziedziczą z kodu.</span><span class="sxs-lookup"><span data-stu-id="24fec-107">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="24fec-108">Pełne przeszukiwanie stosu nie jest przeprowadzane z tym typem popytu i że kod nadal jest podatny na ataki luring.</span><span class="sxs-lookup"><span data-stu-id="24fec-108">A full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="24fec-109">Na przykład jeśli metoda w zestawie A jest chroniona przez żądanie linku, bezpośredni obiekt wywołujący w zestawie B jest oceniany na podstawie uprawnień zestawu B.  Jednak żądanie linku nie będzie szacować metody w zestawie C, jeśli pośrednio wywołuje metodę w zestawie A przy użyciu metody w zestawie B. Żądanie linku określa tylko elementy wywołujące bezpośrednich uprawnień w bezpośrednim wywołującym zestawie musi mieć połączenie z kodem.</span><span class="sxs-lookup"><span data-stu-id="24fec-109">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="24fec-110">Nie określa uprawnień, które mogą być wymagane do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="24fec-110">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="24fec-111">Modyfikatory przeszukiwania <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A> stosu, i <xref:System.Security.CodeAccessPermission.PermitOnly%2A> nie wpływają na ocenę żądań związanych z łączami.</span><span class="sxs-lookup"><span data-stu-id="24fec-111">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="24fec-112">Ponieważ wymagania dotyczące linków nie wykonują przechodzenia stosu, Modyfikatory przeszukiwania stosu nie mają wpływu na wymagania dotyczące linków.</span><span class="sxs-lookup"><span data-stu-id="24fec-112">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="24fec-113">Jeśli dostęp do metody chronionej przez żądanie linku odbywa się za pomocą [odbicia](../reflection-and-codedom/reflection.md), żądanie linku sprawdza natychmiastowy obiekt wywołujący kod, do którego uzyskano dostęp za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="24fec-113">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="24fec-114">Dotyczy to zarówno odnajdywania metody, jak i wywołania metody wykonywanej przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="24fec-114">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="24fec-115">Załóżmy na przykład, że kod używa odbicia do zwrócenia <xref:System.Reflection.MethodInfo> obiektu reprezentującego metodę chronioną przez żądanie linku, a następnie przekazuje ten obiekt **MethodInfo** do innego kodu, który używa obiektu do wywołania pierwotnej metody.</span><span class="sxs-lookup"><span data-stu-id="24fec-115">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="24fec-116">W takim przypadku sprawdzanie wymagań dotyczących linku jest wykonywane dwa razy: jeden kod, który zwraca obiekt **MethodInfo** i jeden raz dla kodu, który go wywołuje.</span><span class="sxs-lookup"><span data-stu-id="24fec-116">In this case, the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24fec-117">Żądanie linku wykonywane na konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżką wykonywania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24fec-117">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="24fec-118">W związku z tym, gdy żądanie linku jest stosowane do całej klasy, nie może chronić dostępu do konstruktora statycznego, chociaż chroni resztę klasy.</span><span class="sxs-lookup"><span data-stu-id="24fec-118">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="24fec-119">Poniższy fragment kodu deklaratywnie określa, że każdy kod łączący się z tą `ReadData` metodą musi mieć `CustomPermission` uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="24fec-119">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="24fec-120">To uprawnienie jest hipotetycznym uprawnieniem niestandardowym i nie istnieje w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24fec-120">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="24fec-121">Żądanie jest wykonywane przez przekazanie flagi **SecurityAction. LinkDemand** do `CustomPermissionAttribute` .</span><span class="sxs-lookup"><span data-stu-id="24fec-121">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="24fec-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24fec-122">See also</span></span>

- [<span data-ttu-id="24fec-123">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24fec-123">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="24fec-124">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="24fec-124">Code Access Security</span></span>](code-access-security.md)
