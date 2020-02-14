---
title: Żądania połączeń
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
ms.openlocfilehash: 31fbd938acb457a4ea803375d18cb1be11d8b287
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217168"
---
# <a name="link-demands"></a><span data-ttu-id="8b993-102">Żądania połączeń</span><span class="sxs-lookup"><span data-stu-id="8b993-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="8b993-103">Żądanie linku powoduje sprawdzenie zabezpieczeń podczas kompilacji just-in-Time i sprawdza tylko bezpośrednio wywołujący zestaw kodu.</span><span class="sxs-lookup"><span data-stu-id="8b993-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="8b993-104">Łączenie występuje, gdy kod jest powiązany z odwołaniem do typu, w tym odwołaniami wskaźników funkcji i wywołaniami metod.</span><span class="sxs-lookup"><span data-stu-id="8b993-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="8b993-105">Jeśli zestaw wywołujący nie ma wystarczających uprawnień do łączenia się z kodem, link jest niedozwolony i podczas ładowania i uruchamiania kodu zostanie wygenerowany wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8b993-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="8b993-106">Wymagania dotyczące linków można przesłonić w klasach, które dziedziczą z kodu.</span><span class="sxs-lookup"><span data-stu-id="8b993-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="8b993-107">Należy zauważyć, że pełne przechodzenie stosu nie jest przeprowadzane z tym typem żądania i że kod nadal jest podatny na ataki luring.</span><span class="sxs-lookup"><span data-stu-id="8b993-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="8b993-108">Na przykład jeśli metoda w zestawie A jest chroniona przez żądanie linku, bezpośredni obiekt wywołujący w zestawie B jest oceniany na podstawie uprawnień zestawu B.  Jednak żądanie linku nie będzie szacować metody w zestawie C, jeśli pośrednio wywołuje metodę w zestawie A przy użyciu metody w zestawie B. Żądanie linku określa tylko elementy wywołujące bezpośrednich uprawnień w bezpośrednim wywołującym zestawie musi mieć połączenie z kodem.</span><span class="sxs-lookup"><span data-stu-id="8b993-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="8b993-109">Nie określa uprawnień, które mogą być wymagane do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="8b993-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="8b993-110">Modyfikatory przeszukiwania stosu <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>i <xref:System.Security.CodeAccessPermission.PermitOnly%2A> nie wpływają na ocenę żądań związanych z łączami.</span><span class="sxs-lookup"><span data-stu-id="8b993-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="8b993-111">Ponieważ wymagania dotyczące linków nie wykonują przechodzenia stosu, Modyfikatory przeszukiwania stosu nie mają wpływu na wymagania dotyczące linków.</span><span class="sxs-lookup"><span data-stu-id="8b993-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="8b993-112">Jeśli dostęp do metody chronionej przez żądanie linku odbywa się za pomocą [odbicia](../reflection-and-codedom/reflection.md), żądanie linku sprawdza natychmiastowy obiekt wywołujący kod, do którego uzyskano dostęp za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="8b993-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="8b993-113">Dotyczy to zarówno odnajdywania metody, jak i wywołania metody wykonywanej przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="8b993-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="8b993-114">Załóżmy na przykład, że kod używa odbicia do zwrócenia obiektu <xref:System.Reflection.MethodInfo> reprezentującego metodę chronioną przez żądanie linku, a następnie przekazuje ten obiekt **MethodInfo** do innego kodu, który używa obiektu do wywołania pierwotnej metody.</span><span class="sxs-lookup"><span data-stu-id="8b993-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="8b993-115">W takim przypadku sprawdzanie wymagań linku odbywa się dwa razy: raz dla kodu, który zwraca obiekt **MethodInfo** i jeden raz dla kodu, który go wywołuje.</span><span class="sxs-lookup"><span data-stu-id="8b993-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b993-116">Żądanie linku wykonywane na konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżką wykonywania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b993-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="8b993-117">W związku z tym, gdy żądanie linku jest stosowane do całej klasy, nie może chronić dostępu do konstruktora statycznego, chociaż chroni resztę klasy.</span><span class="sxs-lookup"><span data-stu-id="8b993-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="8b993-118">Poniższy fragment kodu deklaratywnie określa, że dowolny kod łączący się z metodą `ReadData` musi mieć uprawnienie `CustomPermission`.</span><span class="sxs-lookup"><span data-stu-id="8b993-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="8b993-119">To uprawnienie jest hipotetycznym uprawnieniem niestandardowym i nie istnieje w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b993-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="8b993-120">Żądanie jest wykonywane przez przekazanie flagi **SecurityAction. LinkDemand** do `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8b993-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b993-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b993-121">See also</span></span>

- [<span data-ttu-id="8b993-122">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8b993-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="8b993-123">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="8b993-123">Code Access Security</span></span>](code-access-security.md)
